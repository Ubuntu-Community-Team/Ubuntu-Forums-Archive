---
title: "Renaming network interface"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by wiflye81 on 2006-11-29
Hi,

I'd like to rename my computer network interfaces, because at school we have 4 network cards in each PC, si I'd like to rename the broadcom card (the most used) in /dev/Broadcom.

But, first, no eth* devices in /dev ](*,) and with an udev rule which match when I test it with udevtest, the symlink doesn't appear.

I also tried the iftab but I don't work and I can't find the ifrename tool.

Can anybody help me ? THX

---

### Post by briealeida on 2008-01-11
I know this is super-old but can you try:

ifconfig_eth*_name="name1"
ifconfig_name1="inet xx.xxx.xxx.xx netmask=xxx.xxx.xxx.x"

or something in that vein?

---

### Post by wiflye81 on 2008-01-11
I will try it, thanks for your help, but I will also try to understand why udev don't work (I am very curious about that but no time to test it).

---

