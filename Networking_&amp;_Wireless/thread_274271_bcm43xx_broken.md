---
title: "bcm43xx broken?"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by sgtpepper on 2006-10-09
hi folks,

im using the native driver for a internal bcm4306.

everything seems to work fine at the first glance. but sometimes i got sudden link losses. wouldn't be to bad after all, if it would not sometimes freeze my whole system.
As i am working on my diploma thesis right now, i need to get rid of this problem fast.

This is what dmesg says:
 dmesg | grep bcm43
[17179590.880000] bcm43xx driver
[17179601.680000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
...

and on the commandline it sometime prints :
bcm43xx MAC suspend failure

oh im using this kernel:

Linux  2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

and this driver:

lsmod | grep bcm
bcm43xx               141868  0
ieee80211softmac       31584  1 bcm43xx
ieee80211              38952  2 bcm43xx,ieee80211softmac



can anyone helpme on this?

best regards, Sgt Pepper

---

### Post by kikos on 2006-10-09
I think the bcm43xx methods posted here don't work for everyone.  I used to use the Broadcom 4309 mPCI device.  When it worked, it worked great.  However, it had occasional, yet crippling connection issues:  no matter what I tried, it would not connect to DHCP server.

Fortunately, I had a Intel Pro Wireless 2200 which I insalled, replacing the 4309.  The IPW2200 works like a charm, no connection or disconnect issues.

My advise is to you is this:  Don't bother trying to get the broadcom to work, unless it is a model # that is known to work flawlessly by using a single method.  Otherwise, you will waste precious time trying to get questionable results.

---

### Post by trubblemaker on 2006-10-17
I hate to advice it but for absolute stability it might be better to use ndiswrapper, as the native driver is still experimental and under developement as noted by the todo listed in your error.  There are some links in my signature if your interested

---

