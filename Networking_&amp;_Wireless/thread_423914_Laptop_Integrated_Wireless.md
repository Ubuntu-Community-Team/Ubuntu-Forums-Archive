---
title: "Laptop Integrated Wireless"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by shiznatix on 2007-04-26
Ok here is my story. I had Edgy and could never get my integrated wireless working. When I upgraded to Feisty I found that tool "Windows Wireless Drivers" and installed my driver and behold, my wireless worked... somtimes. It was very spotty but a lot of things where very spotty (such as beryl and playing videos) so I decided to just do a fresh install of Feisty.

Now I just installed Feisty and the first thing I must do is get my wireless working. I installed the "windows wireless drivers" tool again and could not get a driver to install properly so I went to the command line, removed the driver with ndiswrapper, then reinstalled it from the command line. This gave me more success. Before it was saying "Invalid Driver" but now I get this message:

> bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

which is a marked improvement but still no dice. When I run ifconfig the only thing that shows up is my wired network and the light that goes to my wireless does not turn on. When I open the windows wireless drivers utility it says 'hardware present: no' and thats it.

My wireless card is this (output from lspci):
> 06:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

And I am using the driver that I got from the compaq website today.

So, in the end, I am still without wireless working but I know that it can work since I had it running (even though it was crappy) before. Can anyone lend a little hand?

---

