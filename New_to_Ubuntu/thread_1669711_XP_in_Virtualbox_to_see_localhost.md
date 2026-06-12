---
title: "XP in Virtualbox to see localhost?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by facelikebambi on 2011-01-18
Hi

I'm a web developer moving from Windows XP to Linux, but still need to run XP to check sites in IE etc.

I've installed Ubuntu 10.10 and really liking it. Have also set up my LAMP localhost environment in Ubuntu. 

If I run XP in a Virtualbox and open up a web browser, not sure how I'll get it to see localhost on Ubuntu? 

Or am I going about this the wrong way..? :)

Thanks

---

### Post by [Snc] on 2011-01-18
deleted ...

---

### Post by [Snc] on 2011-01-18
> **facelikebambi said:**
> Hi

I'm a web developer moving from Windows XP to Linux, but still need to run XP to check sites in IE etc.

I've installed Ubuntu 10.10 and really liking it. Have also set up my LAMP localhost environment in Ubuntu. 

If I run XP in a Virtualbox and open up a web browser, not sure how I'll get it to see localhost on Ubuntu? 

Or am I going about this the wrong way..? :)

Thanks

no, you are doing it okay, you have to know what type of lan connection you have with your XP machine and what your "localhost" IP is

```
ifconfig -a
```here you can see how VirtualBox set up your network card for the host.

---

### Post by Dutch70 on 2011-01-18
You may want to install "Wine" to run IE.

---

### Post by [Snc] on 2011-01-18
> **Dutch70 said:**
> You may want to install "Wine" to run IE.

Running IE under WINE is "*not just there*" yet, a virtual machine is the better solution, if you count out, that IE9 will not want to run on XP

---

### Post by facelikebambi on 2011-01-18
Thanks. I've just installed XP on a virtual machine (and amazingly impressed...)

So the XP machine has an IP 10.0.2.15 and gateway address 10.0.2.2

It can ping 127.0.0.1 - is that pinging the host machine (Ubuntu)?

---

### Post by facelikebambi on 2011-01-19
Ah I get it now - just needed to go to XP and point my browser at 10.0.2.2

:p

---

