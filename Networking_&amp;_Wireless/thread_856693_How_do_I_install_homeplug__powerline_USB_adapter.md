---
title: "How do I install homeplug / powerline USB adapter?"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by kenbb99 on 2008-07-11
I can't get my NovaTech USB powerline network adapter to connect and as far as I can tell Ubuntu does not recognize it correctly.  I am trying to connect it through a NovaTech powerline bridge to a D-Link DI-LB604 router.  I have another powerline USB adapter connected to an XP machine and that works fine.  I have used this exact adapter with another machine and it worked fine.

NovaTech does not have a Linux driver.  Reading around the forums it appears that others have been able to plug in their adapters and have them recognized and work right away.

lsusb recognizes the device as 09e1:5121 Intellon Corp

Plugging in the device and typing dmesg says:

:new full speed USB device using uhci_hcd and address 5
:configuration #1 chosen from 1 choice
:bad CDC descriptors

I don't know if any of this is relevant.

Solutions? Ideas? Suggestions?

Thanks.

---

### Post by 44tr on 2008-07-19
Also having "bad CDC descriptors" with a USB wireless adapter; Linksys WUSB54GS.  I think I got the driver issue taken care of from another post.  I was informed that the bad CDC descriptors were the problem, but he didn't have time to figure out / remember how to fix them.  Look forward to the answer if it is generic enough to help me.

---

