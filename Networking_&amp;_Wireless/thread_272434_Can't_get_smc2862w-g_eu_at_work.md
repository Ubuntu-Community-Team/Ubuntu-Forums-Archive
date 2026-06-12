---
title: "Can't get smc2862w-g eu at work"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by Kyh31 on 2006-10-06
Hi,

I installed the latest version of ubuntu.
As i can't find any linux-driver for my usk wireless network adapter (smc2862W-G EU), i began to try ndiswrapper.
I already found that this adapter should work with ndiswrapper.

So i downloaded the win-driver and loaded it into ndiswrapper (ndiswrapper -i smc....inf).
This gives no error.
When i do depmod -a, and then modprobe ndiswrapper, it gives no error.
When i look with lsusb, it finds my usb adapter.
With ndiswrapper -l, everything looks ok, except in dmesg i don't see anything about my msc-adapter.
When i look with wiconfig, it doesn't show anything good neither.

Does anybody has some experience with the combination "ubuntu, smc2862W-G EU"?

I really hope to get some help, because i really need my wireless connection. Otherwise i will have to go back to windows, but i'd really like to use ubuntu from now on.

Kind regards,
Kyh31

---

