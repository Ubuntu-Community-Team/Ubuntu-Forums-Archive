---
title: "Help mount Linkstation partition"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by mikeje99 on 2007-02-11
Hi

I tried to install Freelink onto my 250gb Linkstation. The firmware update worked but unfortunately I then set the Linkstation to request a DHCP address and now I can no longer connect to it. I've used a port sniffer but I can't find it as it's not getting an IP address.

I've connected it directly to my Ubuntu workstation and run 'sudo fdisk -l' and below is the output. The problem is I can't mount the file system. I have tried './fix_ext2_magic --fix /dev/hdb1' but get 'Can't open /dev/hdb1'. This happens on hdb1, hdb2 and hdb3.

Please help as I have some family photos on the drive that are very sentimental and I don't have backup (I know supped me).

Device Boot Start End Blocks Id System
/dev/hdb1 1 48 385528+ 83 Linux
/dev/hdb2 49 81 265072+ 82 Linux swap / Solaris
/dev/hdb3 82 30401 243545400 83 Linux

---

### Post by mikeje99 on 2007-02-11
Yep that's right I'm stupid.

I wasn't running as Sudo. Once I did everything worked.

O well you live and learn.

---

