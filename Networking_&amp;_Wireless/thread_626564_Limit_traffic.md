---
title: "Limit traffic"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by rotalever on 2007-11-29
Hi,
I need an application which can limit my network traffic. Let's say I am allowed to create 500GB traffic / month. How can I limit that? If the 500GB are reached all ingoing connections (to certain ports) should be blocked.

---

### Post by jflaker on 2007-11-29
> **rotalever said:**
> Hi,
I need an application which can limit my network traffic. Let's say I am allowed to create 500GB traffic / month. How can I limit that? If the 500GB are reached all ingoing connections (to certain ports) should be blocked.

You may need to call your hosting provider and ask if they can help.  They may be able to put a hard cap on your transfer limit.  After which, your site will sport a "over limit page"....
Usually, providers allow over limits so they can charge fees, unless you say something, this is their policy in most cases.

I have heard complaints with people going over their hosting limit, especially when their website gets some notoriety........you can EASILY exceed your limit in just a few hours or even minutes. 

Your provider will know what can be done to cap your limit.

---

### Post by rotalever on 2007-11-30
Hi,
My provider gives me the possibility to set a traffic limit. The downside is, that this limit will only be checked daily. For example if I set the limit to 450GB/Month and one day it reaches 449GB and the next day I get "digged" or something like that and the traffic goes up to 510GB, I will have to pay for the 10 extra GBs.

But I thought it could be possible to create a custom traffic limiter on a virtual server where I have root access.
I have also read something about iptables and an IPT_QUOTA extension but I am not sure how this works. On my ubuntu Desktop I can modprobe ipt_quota but cannot use it with iptables because the library is not available on the system. The server would be a debian system which is more or less equal to ubuntu.

---

