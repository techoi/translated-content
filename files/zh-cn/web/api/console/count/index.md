---
title: Console.count()
slug: Web/API/Console/count
---
<div>{{APIRef("Console API")}}{{Non-standard_header}}</div>

<p>输出 count() 被调用的次数。此函数接受一个可选参数 <code>label</code>。</p>

<p>{{AvailableInWorkers}}</p>

<p>如果有 <code>label</code>，此函数输出为那个指定的 <code>label</code> 和 count() 被调用的次数。</p>

<p>如果 <code>label</code> 被忽略，此函数输出 count() 在其所处位置上被调用的次数。</p>

<p>例如，下面的代码：</p>

<pre class="brush: js">var user = "";

function greet() {
  console.count();
  return "hi " + user;
}

user = "bob";
greet();
user = "alice";
greet();
greet();
console.count();</pre>

<p>Console 的输出如下：</p>

<pre class="eval">"&lt;no label&gt;: 1"
"&lt;no label&gt;: 2"
"&lt;no label&gt;: 3"
"&lt;no label&gt;: 1"
</pre>

<p>注意最后一行的日志输出：在 11 行对 count() 的单独调用是被当作一个独立事件来处理的。</p>

<p>如果把变量 <code>user</code> 当作 <code>label</code> 参数传给前面调用的 <code>count()</code>，把字符串 "alice" 传给后面调用的 <code>count()</code>：</p>

<pre class="brush: js">var user = "";

function greet() {
  console.count(user);
  return "hi " + user;
}

user = "bob";
greet();
user = "alice";
greet();
greet();
console.count("alice");</pre>

<p>可以看到输出如下：</p>

<pre class="eval">"bob: 1"
"alice: 1"
"alice: 2"
"alice: 3"</pre>

<p>现在可以基于不同的 <code>label</code> 值维护不同的数值。由于 11 行的 <code>label</code> 匹配了两次 <code>user</code> 的值，因此它不会被当作独立的事件。</p>

<h2 id="语法">语法</h2>

<pre class="syntaxbox">console.count([label]);
</pre>

<h2 id="参数">参数</h2>

<dl>
 <dt><code>label</code></dt>
 <dd>字符串，如果有，count() 输出此给定的 <code>label</code> 及其被调用的次数。</dd>
</dl>

<h2 id="规范">规范</h2>

{{Specifications}}

<h2 id="浏览器兼容性">浏览器兼容性</h2>

{{Compat("api.console.count")}}