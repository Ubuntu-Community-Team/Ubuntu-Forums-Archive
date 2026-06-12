---
title: "Intermittent problem with permanent mount of a SAMBA share"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by sa3999 on 2007-06-14
Hello all,

My first post....please be gentle with a forum & Linux noobie !

I have configured my Ubuntu laptop so that it mounts a permanent SAMBA share from a Lacie NAS device (the laptop connects to the NAS device over WiFi. The NAS device itself is plugged into a network port on the wireless router).

I am pretty sure that my config of fstab is correct as the SAMBA share _**does**_ mount successfully sometimes when I boot the laptop. However, other times it does not work.

If I run sudo mount -a, sometimes the NAS share gets mounted and sometimes not. When it does not work, the return in terminal is:

11901: Connection to Lacie_NAS_1 failed
SMB connection failed

The number at the start of the first line varies all the time.

It seems that this is not a problem with SAMBA (because it works sometimes). Looks more like a WiFi / network problem......?

Anyone seen this before? Is there anything I can do to make the connection work 100% of the time on boot-up (without having to go to a wired connection - which is impossible anyway). The WiFi  connection is rock solid (in fact, the stability of the WiFi connection in Ubuntu is MUCH better than WinXP) and I don't think I have experienced a a dropped wireless connection yet. The signal strength varies between about 40 - 50%.

Many thanks in advance.

---

