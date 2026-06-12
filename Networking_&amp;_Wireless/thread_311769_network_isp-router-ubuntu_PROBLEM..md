---
title: "network isp-router-ubuntu PROBLEM."
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by vr.crawler on 2006-12-03
:-({|= 
i have a d-link dl-604 router and i try to split the conection in 2.
the windows machine will conect to the internet, but ubuntu will not ON THE SAME CONECTION, same settings on router, everything. sometimes i make it work after i restart router several times but after a restart is back again. it wont work. i am going postal already :-({|= 
the router is set on dhcp. 
this can be isp problem, ubuntu,..? ..i dont know  :-# 
after a restart , i have to restart router to make it work, and even so it works just "sometimes". i tryed with freebsd, it does the same. 
just with windows works, now thats a sick problem already . what can it be :-| ...?

---

### Post by teaker1s on 2006-12-03
don't take this the wrong way but dlink customer support and product firmware update or lack of=shite.

your problem will be from experisence that ubuntu can't resolve DNS.
this can be resolved by getting your isp dns ip address and setting both router and ubuntu up for static ip and manual DNS entry

I had a Dlink dsl504t and it was a turd,now have cisco based router

---

### Post by stream303 on 2006-12-05
Probably the easiest solution would be to add your isp's dns server addresses into your router's setup page.

If that doesn't work, or you don't have access to the router, the following howto might provide a simple one-line edit to get you operating again:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

---

