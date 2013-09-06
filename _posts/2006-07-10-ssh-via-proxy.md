---
layout: post
title: SSH via Proxy
category:
tags: []
---
{% include JB/setup %}

公司只能通过 http proxy 上网，Solaris 里面自带的 ssh-http-proxy-connect 命令不
管用，想到 dreamhost 提供的 shell 中摆弄几下总也不成功。今天 google 到一个东西
可以说是最好的解决办法：goto-san-connect 1.96，比<a
href="http://joyus.org/2006/01/ssh-over-proxy/">以前发现的http tunnel</a>方便多
了。

源码：<a href="http://zippo.taiyo.co.jp/%7Egotoh/ssh/connect.c">http://zippo.taiyo.co.jp/~gotoh/ssh/connect.c</a>

编译方法源码里就有。

用于 openssh 时在 ~/.ssh/config 里用 ProxyCommand 命令，例如：

<pre>
Host joyus
    User <i>fakename</i>
    Hostname joyus.org
    ProxyCommand connect -4 -H <i>proxyserver</i>:<i>port</i> %h %p
</pre>

更多信息：

Using OpenSSH through a SOCKS compatible PROXY on your LAN
<a href="http://zippo.taiyo.co.jp/%7Egotoh/ssh/openssh-socks.html">http://zippo.taiyo.co.jp/~gotoh/ssh/openssh-socks.html</a>
<br>
Detailed usage
<a href="http://zippo.taiyo.co.jp/%7Egotoh/ssh/connect.html">http://zippo.taiyo.co.jp/~gotoh/ssh/connect.html</a>