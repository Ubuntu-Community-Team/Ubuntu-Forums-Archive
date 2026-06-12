---
title: "TCP congestion algorithm"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by Looza on 2006-12-04
Hi,

I've been trying to change the tcp congestion algorithm with the command: ```
sysctl -w net.ipv4.tcp_congestion_control=westwood
``` but I can't seem to use any algorithm beside bic(default) and reno.
Does anybody know why and what to do to add other algorithms?

Thanks.

---

### Post by ciscosurfer on 2006-12-04
> **Looza said:**
> Hi,

I've been trying to change the tcp congestion algorithm with the command: ```
sysctl -w net.ipv4.tcp_congestion_control=westwood
``` but I can't seem to use any algorithm beside bic(default) and reno.
Does anybody know why and what to do to add other algorithms?

Thanks.I'm not totally sure.  But maybe these will help you:

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/configtuning-sysctl.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/configtuning-sysctl.html)
[http://www.google.com/search?q=net.ipv4.tcp_congestion_control&ie=utf-8&oe=utf-8&rls=Swiftfox:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=net.ipv4.tcp_congestion_control&ie=utf-8&oe=utf-8&rls=Swiftfox:en-US:unofficial&client=firefox-a)

Aha! This might help: [http://c3lab.poliba.it/index.php/Westwood:Linux](http://c3lab.poliba.it/index.php/Westwood:Linux)

---

### Post by Looza on 2006-12-05
Thanks for the sites but I've been to most of them. And most of the sites hint that the kernel already comes with some algorithms but I can't use any of them beside reno and bic.
What I want to know is if I need to patch my kernel or if there is any other way that I can make the other algorithms to work.
Can anyone help me?

-- Edit --

In fedora its possible to change the tcp congestion algorithm to other algorithms beside bic and reno.
Can anyone tell me what do I have to do to be able to use other algorithms?

---

### Post by spx3 on 2006-12-05
just code your own :-D

---

### Post by Looza on 2006-12-05
> **spx3 said:**
> just code your own :-D
Thanks, thats very helpfull.

I downloaded a new version of the kernel and I'm compiling it with all tcp algorithms the the kernel supports. Thanks everyone for the help.

---

