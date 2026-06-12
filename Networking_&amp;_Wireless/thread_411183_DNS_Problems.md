---
title: "DNS Problems?"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by AusIV4 on 2007-04-16
I'm having a strange problem right now. I was browsing the web, when all of the sudden Firefox started giving me "unable to connect" errors on everything on the web. I was able to contact other computers on my network, and the other computers on the network are able to connect to the website.

I assume this is some kind of DNS error on the troubled machine. Is there any way to find out what DNS server is being used?
[EDIT]
Suspending then resuming seems to fix the problem for a few minutes, but then it comes back.

---

### Post by dbott67 on 2007-04-16
You can check the output of the following command:
```
dbott@feisty:~$ cat /etc/resolv.conf 
naemeserver 192.168.1.1
```If you are using a home router (DSL/Cable router) then it may be the problem.  Many cheaper routers choke on IPv6, so disabling it on your machine helps in many cases.  The other thing to try is changing your DNS servers to the OpenDNS servers.

Check this thread, post #3 and #5.
[http://ubuntuforums.org/showthread.php?t=323747](http://ubuntuforums.org/showthread.php?t=323747)

-Dave

---

### Post by PurplePenguin on 2007-04-16
This is a weird problem that seems to be affecting a lot of us lately... Dave's link explains the fix, but you can go straight to [OpenDNS's Ubuntu-specific instructions]("http://www.opendns.com/start/ubuntu.php") if you'd like.  I'm almost certain that this quick fix is exactly what you need.

---

### Post by CrankyFilipino on 2007-07-11
> **PurplePenguin said:**
> This is a weird problem that seems to be affecting a lot of us lately... Dave's link explains the fix, but you can go straight to [OpenDNS's Ubuntu-specific instructions]("http://www.opendns.com/start/ubuntu.php") if you'd like.  I'm almost certain that this quick fix is exactly what you need.

Yes I know it's an old thread.. but I would just like to say thank you for this link.. finally I got the DNS changed.. I've been trying forever.. I mean my router is already set to OpenDNS but that didn't even work.. and I never thought to look on their website.. anyways thanks man!

---

