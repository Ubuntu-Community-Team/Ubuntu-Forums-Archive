---
title: "Partitioning a Hardrive."
date: 2009-05-18
forum: New to Ubuntu
---

### Post by nava2 on 2009-05-18
I'm brand new to this whole deal, so please, bare with me. 

So, I just installed Ubu 9.04. I can't install anything as, being new, I didn't partition my hard drive when I installed. 

How can I partition it now as the /dev/sdf2 partition is locked! I already freed up space using GParted, and now I just need to expand /sdf2 into the newly allocated space.

Any help is appreciated;

-n2

E: sorry for not searching, I couldn't find much of help.. Everyone elses just seems to work! :(

---

### Post by billgoldberg on 2009-05-18
> **nava2 said:**
> I'm brand new to this whole deal, so please, bare with me. 

So, I just installed Ubu 9.04. I can't install anything as, being new, I didn't partition my hard drive when I installed. 

How can I partition it now as the /dev/sdf2 partition is locked! I already freed up space using GParted, and now I just need to expand /sdf2 into the newly allocated space.

Any help is appreciated;

-n2

E: sorry for not searching, I couldn't find much of help.. Everyone elses just seems to work! :(

To make things a bit more clear for us, please open a terminal (applications, accessories, terminal) and enter this command:

```
sudo fdisk -l
```

Use the password you sign in with when you are prompted for it and press enter. You won't see what or how many letters you type.

Then post the outcome of the command here.

---

### Post by nava2 on 2009-05-18
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52ce52ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81a5c41b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       57925   465282531    7  HPFS/NTFS
/dev/sdf2           60476       60801     2618595    5  Extended
/dev/sdf5           60476       60779     2441848+  83  Linux
/dev/sdf6           60780       60801      176683+  82  Linux swap / Solaris
```

That?

---

### Post by billgoldberg on 2009-05-18
If you use the Ubuntu live cd and make sure no drives are mounted, merging the two partitions should work.

(gparted is on the Ubuntu live cd, press alt+f2 and enter: gksu gparted)

---

### Post by Don1500 on 2009-05-18
(gparted is on the Ubuntu live cd, press alt+f2 and enter: gksu gparted)
Can you do that before you boot into the cd?

---

### Post by Paqman on 2009-05-18
> **billgoldberg said:**
> 
(gparted is on the Ubuntu live cd, press alt+f2 and enter: gksu gparted)

Er, it's also in the menus dude. System > Admin > Partition Editor.

---

### Post by jrox717 on 2009-05-18
> **Paqman said:**
> Er, it's also in the menus dude. System > Admin > Partition Editor.
Partition Editor doesn't seem to be on my menu...

(I just upgraded to 9.04)

---

### Post by Mark Phelps on 2009-05-19
> **nava2 said:**
> How can I partition it now as the /dev/sdf2 partition is locked! I already freed up space using GParted, and now I just need to expand /sdf2 into the newly allocated space.

According to your fdisk listing, sdf2 IS already extended to cover the remainder of the space on the device.  It starts at 60476 (beginning of sdf5) and ends at 60801 (the end of sdf6).

If you're talking about extending sdf2 FORWARD to incorporate the space currently occupied by sdf1, you can't because they're different kinds of partitions.

So, not sure what you're really trying to do...

Also, GParted is not installed by default.  You need to go into Synaptic and select GParted to install it. However, a better way to do partition work is to download and burn the GParted LiveCd from distrowatch.com.  It is a newer version than the one bundled with the distros and it avoids the problem of having partitions mounted while you;'re running it.

---

### Post by mapes12 on 2009-05-19
Two physical HDD's with first one reported correctly as sda but second one as sd_f_? What happened to sdb which should be the usual naming policy?

Would I be correct in assuming that you have windoze on the first HDD and are trying to install Ubu on the second disk? 

As stated previously, loading a GParted LiveCD should help you reconfigure these partitions correctly.

---

