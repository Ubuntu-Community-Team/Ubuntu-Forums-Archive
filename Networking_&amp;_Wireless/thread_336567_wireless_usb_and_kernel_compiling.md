---
title: "wireless usb and kernel compiling"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by haggus on 2007-01-11
Ok I have Ubuntu 6.10 running kernel 2.6.17.10 generic I'm trying to upgrade the kernel to 2.6.18.2 everything went well using the guide and I installed the new custom kernel image and linux headers everything went it as it should first time reboot and I'm in the new kernel only thing is my dlink wireless usb  won't work I'm using ndiswrapper and it shows my driver installed but no network card to configure. Anyone have suggestions on how to fix this?

---

### Post by doobit on 2007-01-11
Which chipset is the wireless adapter?

---

### Post by haggus on 2007-01-11
the usb is a dwl g122 rev a2 The DWL-G122, however, uses a Ralink Technology 2500 series chipset

---

### Post by doobit on 2007-01-12
> **haggus said:**
> the usb is a dwl g122 rev a2 The DWL-G122, however, uses a Ralink Technology 2500 series chipset

I know the Ralink chipsets were working with Ndiswrapper before. I had a little trouble compiling the 2.6.18.2 kernel because there were so many module selections compared to 2.6.18.1 which was much more automatic. I think 2.6.19 and later are supposed to have better wireless detection as well.
There is also a confirmed bug:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34902](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34902)

I hope there is someone who has had some more experience here with that chipset who can help you.

---

