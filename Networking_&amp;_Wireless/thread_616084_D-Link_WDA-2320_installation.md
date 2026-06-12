---
title: "D-Link WDA-2320 installation"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by Donnut on 2007-11-17
Hi.  I just bought a wifi PCI card, but it won't show up!  How do I install with a windows driver?
steve@steves-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

steve@steves-desktop:~$

---

### Post by Donnut on 2007-11-17
OK, Also, how do I install ndiswrapper?  I think I can get my driver installed then.

---

### Post by mocha on 2007-12-10
I have that same card working flawlessly under Feisty.  You need to enable restricted drivers.  You probably do not have the restricted modules loaded on your system.  Look in synaptic for linux restricted modules.

---

