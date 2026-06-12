---
title: "Partition Resizing"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-02-01
(Skip if you want) I'm finally dual-booting windows and ubuntu, with ubuntu installed first, and I gotta say that it was much easier dual-booting than when I tried to dual-boot with windows installed first.

Anyway, because of iTunes I have to transfer all of my songs -totalling only 1.2Gb- onto my Windows Partition. Would it be safe to reinsert my Live CD version of ubuntu and repartition my main HDD to give Windows about 1.5Gb more on it's partition? I'm pretty sure it is, but I wanna be certain.

---

### Post by caljohnsmith on 2009-02-01
It would be good to first see the physical layout of your partitions to know if that is possible, so how about posting the output of:
```
sudo fdisk -lu
```
And we can go from there if you want.

---

### Post by mattbutsko on 2009-02-01
Well, I realized that since I do have a tiny music collection and I have a 12Gb windows partition for GuildWars and iTunes, I shouldn't really *need* to resize. But I will write that command down. Thanks!

---

### Post by mattbutsko on 2009-02-01
Okay, scratch that. I will definitely need to resize this partition.

I've yet to know what it means but here's the output for fdisk:

```
Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x50c0b2fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    52532549    26266243+  83  Linux
/dev/sda2   *    52532550    77031674    12249562+   7  HPFS/NTFS
/dev/sda3        77031675    80405324     1686825    5  Extended
/dev/sda5        77031738    80405324     1686793+  82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders, total 40188960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c5b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    40178564    20089251   83  Linux

Disk /dev/sdc: 2048 MB, 2048729600 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001425 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             245     3999743     1999749+   6  FAT16

```

---

### Post by caljohnsmith on 2009-02-01
Actually, trying to take space from your Ubuntu partition to give to your Windows partition could definitely be a problem. The reason is because your Ubuntu partition is before your Windows partition; if you shrink Ubuntu and give the space to Windows, you will be moving the starting sector of the Windows partition, and unfortunately that usually breaks Windows. If you have Vista rather than XP, moving the starting sector of the Vista partition may work out OK, because I've seen some people with Vista move the starting sector and actually get Vista booting afterwards without too much effort. But the bottom line is if you want extra space for Windows, I would recommend deleting your sda5 swap partition, and then you can add that 1.6 GB worth of space onto the end of your Windows partition; that will be a lot less risky than moving the starting sector of the Windows partition. Then you can shrink your sda1 linux partition by 1.6 GB (or however much you want for swap), and create a new swap partition in that space. There will be only a few commands you need to run in order to get Ubuntu to use the new swap partition, so that should be really easy. So how about trying those partition changes and let me know how it goes.

---

### Post by theozzlives on 2009-02-01
You could install ext2fck in Windows to access your Ubuntu partition from Windows If your music will fit there.

---

### Post by mattbutsko on 2009-02-02
Both options sound good. I will try both when I'm back on my main computer. Thanks a lot.

---

### Post by mikechant on 2009-02-03
*If you have Vista rather than XP, moving the starting sector of the Vista partition may work out OK, because I've seen some people with Vista move the starting sector and actually get Vista booting afterwards without too much effort.*


When I did this, there was *no* effort on my part involved - apart from not giving in to the feeling that I'd screwed up Vista and hitting the power switch.
When I booted Vista it sat for about 3 hours on a blank screen apparently doing nothing (but actually doing some sort of mega filesystem check/repair). Then it booted up fine as if nothing had happened.
This actually happened when I shrank the Vista partition *at the end*, because Gparted decided the *start* of the Vista partition wasn't correctly aligned and moved it very slightly as well!

---

