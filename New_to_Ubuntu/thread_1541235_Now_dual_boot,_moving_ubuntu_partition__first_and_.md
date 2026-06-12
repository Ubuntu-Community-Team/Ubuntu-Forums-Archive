---
title: "Now dual boot, moving ubuntu partition  first and remove window xp in first partition"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by seuzo on 2010-07-28
Hi,

Now having dual boot.
Which first partition is window xp and second partition is ubuntu 10.4.

Wanna to remove window xp and move ubuntu 10.4 to only os in my laptop. Is it possible without flash installation?

Thank you.

---

### Post by tachyon4 on 2010-07-29
gparted should be able to format your windows partition and grow your ubuntu partition.  you shouldn't need to reinstall ubuntu.  just be sure to backup your files (obviously from windows, but also from ubuntu to be safe).

---

### Post by beew on 2010-07-29
> **tachyon4 said:**
> gparted should be able to format your windows partition and grow your ubuntu partition.  you shouldn't need to reinstall ubuntu.  just be sure to backup your files (obviously from windows, but also from ubuntu to be safe).

Are you sure? I think there are at least two issues. 

1) XP is installed before Ubuntu so the XP partition would be to the left of the Ubuntu one. I can be wrong, but I think you can't expand your Ubuntu partition to the left.

2) In this configuration it seems that the windows partition would be the boot partition of the hard drive which contains GRUB2. Delete it and your computer wouldn't boot anymore.

I can be wrong since I am very new to this myself, but I would be rather cautious about it ( I have a dual booting computer in the same configuration: XP first and then Ubuntu, I too am thinking of getting rid of XP)

---

### Post by jtarin on 2010-07-29
> **beew said:**
> Are you sure? I think there are at least two issues. 

1) XP is installed before Ubuntu so the XP partition would be to the left of the Ubuntu one. I can be wrong, but I think you can't expand your Ubuntu partition to the left.

2) In this configuration it seems that the windows partition would be the boot partition of the hard drive which contains GRUB2. Delete it and your computer wouldn't boot anymore.

I can be wrong since I am very new to this myself, but I would be rather cautious about it ( I have a dual booting computer in the same configuration: XP first and then Ubuntu, I too am thinking of getting rid of XP)
I'm thinking you could shrink the partition to a size that you could reinstall Grub ,if need be, to (MBR)in its own partition. Remember to make it active (bootable), then expand your Linux partition.[Grub Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm")

---

### Post by bumanie on 2010-07-29
As long as you don't change the name (or UUID) of the ubuntu partition, you should be able to delete windows, then use gparted to extend your linux partition and then do > sudo update-grub in terminal. OS prober should recognise that xp is no longer there and reconfigure grub accordingly. Of course, as already stated, back up important things first, there is always a small risk of things going wrong during partitioning, especially an unexpected power failure or something similar, although with a laptop, ensure the battery is full before starting, use a.c and if a power failure occurred, hopefully the battery would take over and last long enough to finish the partitioning. Moving partitions can take a long time, depending on the size of the partition and how much data needs to be moved.

---

