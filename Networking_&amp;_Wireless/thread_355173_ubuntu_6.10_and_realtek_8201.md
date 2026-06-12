---
title: "ubuntu 6.10 and realtek 8201"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by billionmonkeys on 2007-02-06
I'm trying to install ubuntu 6.10 on an asrock motherboard (AM2NF6G-VSTA).  This motherboard has a Realtek PHY RTL8201CL lan chip onboard, but ubuntu doesn't set up eth0 against it.

lsmod shows the sis900 driver is loaded, I assume this is the right driver for this lan device?

is fixing this just a matter of setting up some alias in /etc/modprobe.d ?

lspci doesnt show any realtek device at all (it does on my laptop that has a realtek 8139)

any ideas?

---

### Post by billionmonkeys on 2007-02-24
Since I've solved this myself, I'll post a reply in case anyone ends up here.  The issue is that the motherboard is an nforce4 board, which is only supported in 2.6.18 and above, so in order to get everything working you have to upgrade to a 2.6.18 or higher kernel.  There are other helpful threads on this topic if you search for nforce4.

---

### Post by cenwesi on 2007-03-09
could you elaborate.... i installed v6.10 and i don't have sound or net??? not to mention some unknown hardware/device in the device manager.

---

