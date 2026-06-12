---
title: "Realtek 8139 eth0 inteface won't load after Edgy update"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by wsanders on 2006-11-01
I updated a system running Ubuntu server to Edgy, and now it does not load my ethernet card. It worked before the upgrade. The chipset name shows up in lspci, but the only interfaces shown in ifconfig -a are lo and sit0. I've modprobed the chipset drivers, no luck.

Any ideas on getting this working?

---

### Post by Sodki on 2006-11-03
I had the same problem as you. Try adding pci=noacpi to the kernel options in /boot/grub/menu.lst.

---

