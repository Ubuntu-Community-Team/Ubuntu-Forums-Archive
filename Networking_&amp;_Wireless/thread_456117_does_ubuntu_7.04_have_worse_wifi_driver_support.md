---
title: "does ubuntu 7.04 have worse wifi driver support?"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by bone2006 on 2007-05-27
I put ubuntu 7.04 on one machine and was having trouble with ndiswrapper, and didn't think much about it.
Then I went to an older machine that has a D-link Air DWL-520 wireless PCI Adapter (rev d) installed.  I haven't had any problems with 4 or 5 other distros I have thrown at this machine and I've used ubuntu 6.10 without any requirements to install any drivers.
Now after install ubuntu 7.04 wifi device doesn't show up in the network tool and I tried typing in the command iwconfig and nothing.

---

### Post by bone2006 on 2007-05-27
I rebooted my machine just now into ubuntu to get the lspci info and it said you are now connected to a network.  Funny how I have two wired ethernet ports and one pci wifi card in there and there's no wires going to the computer, so not sure how it thinks it's connected?

Here's what it says about my card:
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
Subsystem: D-Link System Inc Unknown device 3303
Flags: bus master, medium devsel, latency 32, IRQ 11
I/O ports at 9400 [size=256]
Memory at e0010000 (32-bit, non-prefetchable) [size=256]

---

### Post by bone2006 on 2007-05-27
Just incase anybody else has the same problem, I thought I'd post what I had to do to get it to work.

the only thing that seemed to work was going to ndiswrapper's website getting version 1.44 stable and compiling it on my machine and installing it, then everything worked.  It's a shame that other people are having problems as well with their wifi and seems something ubuntu did with the new version compared to the last version.  

There's plenty of people who are trying to give linux a try and personally wifi/internet is something that if they don't get it to work right away, it's a show stopper.

---

