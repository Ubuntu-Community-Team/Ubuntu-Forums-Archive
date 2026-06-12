---
title: "Booting XP SP3"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by THIS_IS_INSANE on 2011-06-27
[SIZE=2]I installed Ubuntu last night on my computer running XP SP3. I did a side-by-side install. I have two hard drives, one is a maxtor 80gb IDE, and the other is a seagate 1.5TB SATA. I split the Seagate drive into two partitions, one for ubuntu's primary drive, and the other as a logical partition for both OS's (XP boots off of the Maxtor). When I turn my computer on, there is no OS selection menu, it only boots straight to Ubuntu. How do I boot XP?
[/SIZE]

---

### Post by wolfen69 on 2011-06-27
In ubuntu, do:
```
sudo update-grub
```
and reboot.

In the BIOS, make sure the ubuntu drive is the first one to boot.

---

