---
title: "Wireless Problem"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by psudangert on 2008-02-24
I just installed ubuntu 7.10 on my new dell inspiron 1520. Wireless networks aren't showing up anymore (most importantly my own). In other posts, I wan't able to find a suitable solution, but many asked to start off by running lspci, so I've included that below. Thank you for any help!

andrew@andrew-laptop:~$ lspci -nn | grep Network
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

---

### Post by Hightide on 2008-02-24
Hi Psudangert

I see from lspci you have a Broadcom Card.Try [this]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")


regards

:)

---

