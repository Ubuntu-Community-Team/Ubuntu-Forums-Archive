---
title: "Kubuntu 15.04 Dell with broadcom wireless keeps disconnecting, crashes after suspend"
date: 2015-06-05
forum: Networking &amp; Wireless
---

### Post by ozeuss2 on 2015-06-05
I've used 14.10 and 15.04 Kubuntu with this Dell inspiron, and I had wireless crashing after suspend regularly, but I managed with just restarting wireless. But the last couple of days I have wireless crashing every couple of minutes without warning or notification - my connection just stops and when I re-scan the wifi, it shows just my network. Restarting sometimes work, but sometimes I need to restart network manager.
My problem persists through several networks, and not experienced in my OEM Win8.

I'm attaching my wireless info. I've went over Chili555's broadcom guide, and I'm using bcmwl-kernel-source.

---

### Post by sam1948 on 2015-10-15
Run on cli "uname -a" 
and see if you have 64bit installation.
Mine is this: 
"Linux dell-lapt 3.19.0-30-generic #34-Ubuntu SMP Fri Oct 2 22:08:41 UTC 2015 **x86_64** x86_64 x86_64 GNU/Linux"
Make sure you have x86_64 there.
If you have the 32bit try running 64bit from a live usb and see if it works for you (before fully installing)

** I've seen many creashes when I was using the 32bit installation (by mistake)

---

