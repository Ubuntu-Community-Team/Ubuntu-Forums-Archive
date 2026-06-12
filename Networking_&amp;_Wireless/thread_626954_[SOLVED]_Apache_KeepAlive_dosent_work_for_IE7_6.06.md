---
title: "[SOLVED] Apache KeepAlive dosent work for IE7 6.06 LTS"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by hanso on 2007-11-29
Hello,

now after we have more users, we have a problem with performance.
The load rises up to 10 and web sites are deliverd very slow.
But the reason is not, that any special type of process consumes CPU or IO.

In investigation on this, I found out with netstat, that we have many TCP connections from the same client  at a time (20-40). In total 300-400.

Further I did find out that loading a Webpage with IE 7 produced as much connections, as are files (images) in the page. But with Firefox there are only 1-2 connections.

In the apache config KeepAlive ist set to On.
An other Server with Apache2  based on Suse 9.1  dosent show this problem with any Browser.

What can I do to solve this problem.

Hans

---

### Post by hanso on 2007-11-30
In mod_ssl.conf nokeepalive is enabled for MSIE.
Unfortuneally this works for all  MSIE connections, not only SSL.

To solve the problem remove this driective.

Hans

---

