---
title: "Does GRUB and Ubuntu like RAID0?"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-12-16
Short Question version:
Does having a dual boot (Windows & Linux) work with a RAID0?



Long detailed version:
I'm going to run RAID0. This is through an ASUS MOBO w/Silicon Image 5723 onboard RAID chipset that has Windows software that works with the RAID0. I assume so windows can see it without the need for a floppy disk drivers.

Im not sure if I shrink the HDD for Ubuntu if it will like that. 

I have a data HDD that will not be on the RAID, I could put it on there, shrinking that instead of the RAID.

Also, should I have it put GRUB on the Data HDD instead of the RAID0?

---

### Post by stefangr1 on 2008-12-16
I understand that you wan't  the shrink your windows RAID0 partitions, and install ubuntu on it?

The best way to do so would be to create a small regular partition for /boot (100mb) and use the rest to create a software raid0 array on the rest of the emptied space, using the ubuntu alternate install cd. Both performance and security of the software raid is slightly better than that of the fake raid of a motherboard. When you install grub on the boot partition or on the mbr, everything should go fine.

---

### Post by caljohnsmith on 2008-12-16
I think it is likely that Ubuntu will see your drives as separate, and not in their RAID0 configuration. You can check by booting your Ubuntu Live CD (the install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And if that shows your two drives with one of the drives not containing a partition table, then Ubuntu sees your drives as separate. If that's the case, you might want to check out this tutorial:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Anyway, good luck and let us know how it goes. :)

---

