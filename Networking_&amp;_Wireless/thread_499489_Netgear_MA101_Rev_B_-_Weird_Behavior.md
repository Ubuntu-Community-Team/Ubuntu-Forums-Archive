---
title: "Netgear MA101 Rev B - Weird Behavior"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by superblahblah00 on 2007-07-12
Hi, I'm pretty new to ubuntu so I dont know if I'm missing something obvious.
That said, here is the problem:

I have an older Dell Dimension Desktop with a 2.4GHz Pentium 4 and 512 MB of ram. It connects to the internet wirelessly, using a netgear ma101 usb revison B. I was pleasantly surprised when Feisty picked up the wireless card and autoconfigured it. However, after a few hours the machine would randomly lock up. The at76_usb driver that it was using also interfered with NVIDIA driver that I was attempting to install. So installed NDISwrapper, and that also solved both problems.

Except, now the ndiswrapper driver causes a kernel panic every day. If I recompile the driver and re-insert it, the computer will work fine for that particular day. But the next day, it returns to its previous, kernel panic inducing, stage.  The output of the kernel panic says lots of stuff about SMP, and that got me wondering why I have an SMP kernel on a single processor machine.

I'm thoroughly stumped. Any ideas on how to fix this?

---

### Post by Het Irv on 2007-07-12
I am very new and this probly wont help much but did you do the step that tells Ubuntu to load NDISWrapper on boot.  Like i said im new and dumb so thats probly not it

---

### Post by superblahblah00 on 2007-07-14
It loading is the problem. It happened again today, the previously working driver caused a panic. I'm at my wits end.......

at76_usb locks up after a few hours and breaks the NVIDIA driver....
ndiswrapper needs to be reinstalled every day.....

argh.

---

