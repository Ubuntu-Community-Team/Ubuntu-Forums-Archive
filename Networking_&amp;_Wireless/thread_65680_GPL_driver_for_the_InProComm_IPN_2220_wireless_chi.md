---
title: "GPL driver for the InProComm IPN 2220 wireless chipset"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by ringe on 2005-09-14
Great news: I've found a GPL driver for the InProComm IPN 2220 wireless chipset at [ftp://ftp.dlink.com/GPL/di624M/di624m_fw10_source.tar.gz](ftp://ftp.dlink.com/GPL/di624M/di624m_fw10_source.tar.gz). Now, I can't use it directly (can I?) - or how do I use it?

The driver is a 2.4 kernel patch. I don't think I know enough to do anything with it.

---

### Post by mlomker on 2005-09-14
Nope, especially since we use a 2.6 kernel these days.

Read [this thread](http://www.ubuntuforums.org/showthread.php?t=34934&highlight=ipn2200+driver).  It can work with the proper ndiswrapper driver.

---

### Post by ringe on 2005-09-14
Thanks. I wrote this:

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsPackardBell?highlight=A5560](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsPackardBell?highlight=A5560)

The driver needs to be ported, I guess. I sent an email to LKML.

---

### Post by alek66 on 2006-12-03
so....thsi means I dont have to use ndiswrapper anymore???
How can i get the native for my kernel?

---

### Post by tbfr on 2006-12-16
> **alek66 said:**
> so....thsi means I dont have to use ndiswrapper anymore???
How can i get the native for my kernel?

There isn't a native driver. You will have to use NdisWrapper.

---

### Post by TTL on 2007-02-17
Well the mentionend Archive-File does contain a native linux driver for the IPN2220. However the driver is not GPLed. It is an object file with headers but without the source. :-(

---

