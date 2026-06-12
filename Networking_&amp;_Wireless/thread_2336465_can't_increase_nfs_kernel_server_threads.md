---
title: "can't increase nfs kernel server threads"
date: 2016-09-08
forum: Networking &amp; Wireless
---

### Post by ewuewu on 2016-09-08
Hi there,

I've just installed ubuntu 16.04 on my new box. I'm using it as nfs server and would like to run it with 32 threads..
Now I'm trying to increase [FONT=arial]RPCNFSDCOUNT in /etc/default/nfskernelserver to 32 (I've also tried it in /etc/init.d/nfs-kernel-server) but after restart I alwyas see only 8 threads.

If I remember correctly it was working under 14.04.

Any ideas?
[/FONT][COLOR=#545454][FONT=arial]

[/FONT][/COLOR]

---

### Post by qrz73 on 2016-09-20
Hello.

This not an answer, but how do you see how much threads you have and why you decided it's not enough ?

---

