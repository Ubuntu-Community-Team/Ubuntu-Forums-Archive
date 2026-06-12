---
title: "Uh oh... Grub doesn't see Windows anymore."
date: 2011-03-18
forum: New to Ubuntu
---

### Post by jhargis1012 on 2011-03-18
Hello. Earlier today, I had Ubuntu 10.10 and Windows 7 working next to each other just fine. I wanted to give Lubuntu a try and I also wanted to resize my partitions a bit. In Windows, I used Easeus Partition Master to shrink the Ubuntu partition and then integrate that into the Windows one. Upon reboot, grub was broken. I assume shrinking the Ubuntu partition in Windows did this. This was fine though, because I wanted to install Lubuntu. So I popped in the Lubuntu USB stick and did a full install on the remains of the old Ubuntu partition. After updating, I tried to shutdown and boot into Windows... only to find it was gone from the grub menu! Now, I could be remembering incorrectly, but I feel like the Windows partitions were there BEFORE the update.

Ideally, grub should show Lubuntu and then Windows below that (I think there were two separate partitions for Windows, one for system and one for everything else... but I can't remember if this showed up in grub) and then finally the Windows recovery partition (which I'd really like to get back!).

Here's some code:

```
jeremy@jeremy-TOSHIBA-NB205:~$ sudo fdisk -l
[sudo] password for jeremy: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74457445

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192        6565    51196338+   7  HPFS/NTFS
/dev/sda3           18488       19458     7790592   17  Hidden HPFS/NTFS
/dev/sda4            6566       18488    95765505    5  Extended
/dev/sda5            6566        6690      999424   82  Linux swap / Solaris
/dev/sda6            6690       18488    94765056   83  Linux

Partition table entries are not in disk order
jeremy@jeremy-TOSHIBA-NB205:~$ 

```

I would greatly appreciate any guidance. Thank you.

---

### Post by drs305 on 2011-03-18
For some reason Lubuntu doesn't include os-prober, which is needed to find other OS's. Install it and update Grub2 and it should find Windows.

```
sudo apt-get install os-prober
sudo update-grub
```
As the update-grub command is running, watch and you should see a reference to Windows as the partitions are searched.

---

### Post by jhargis1012 on 2011-03-18
Wow, thank you very much, it worked like a charm. Good to know in the future!

---

