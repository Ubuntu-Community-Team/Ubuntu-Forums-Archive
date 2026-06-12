---
title: "partitioning problem"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by patchido on 2009-05-07
i own a dell inspiron 1420, and a sata EXT HD of 60 gib, in my laptop y have vista by default, and becuase the laptop is "family's" i cant put ubuntu in it, thats why i got this EXT long time ago, i installed intrepid when it was barely out and been using it, but know i needed xp to play some games (there is no alternative) and i did a partition in my EXT for it, everything went fine by now, the problem is that i had to be changing HDs to install and not damage MBR form primary disk so i placed the EXT into the laptop as internal, and installed xp, and i returned grub and i can run XP from GRUB, but when i placed the HDS as they were suposed to go, meaning EXt being an EXT when i try to log into windows it crashes when loading, and if i pop the external into an internal it does work, this is really alward and really need help. i need to be able to run xp as an external.

plz help

here i post my fdisk while EXT is in internal:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed260086

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5080    40805068+  83  Linux
/dev/sda2   *        5081        6992    15358140    7  HPFS/NTFS
/dev/sda3            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```

and here is my grub menu

```


title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c209b65b-ace7-430f-bda0-e9ee0ac2c2ef
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c209b65b-ace7-430f-bda0-e9ee0ac2c2ef ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c209b65b-ace7-430f-bda0-e9ee0ac2c2ef
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c209b65b-ace7-430f-bda0-e9ee0ac2c2ef ro  single
initrd		/boot/initrd.img-2.6.27-11-generic


title		Ubuntu 8.10, memtest86+
uuid		c209b65b-ace7-430f-bda0-e9ee0ac2c2ef
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Guindows Xp
root		(hd0,1)
savedefault
chainloader	+1

```

---

### Post by dborba on 2009-05-07
Hey there! I suspect your problem is that since when you set up grub your external drive was the only drive on the computer, grub was configured with it being the primary (only drive). Then, when you load it up as a secondary drive, it is getting confused.

I don't know of an exact solution of the top of my head, but I suspect that in your grub menu, xp should not be set as hd0 since that is likely your regular internal drive.

As a side question, are you still able to boot into ubuntu from grub when using the regular internal drive & the external?

---

### Post by patchido on 2009-05-08
yes

---

### Post by dborba on 2009-05-08
Well no idea if it will work, but you can always try to change the XP setting to hd1 from hd0.

Also another question. When you boot, do you just have your bios use the external as the primary boot device when it's plugged in, or do you select to boot from it in another fashion?

---

### Post by patchido on 2009-05-08
external is primary

---

### Post by patchido on 2009-05-08
actually i dont think there is a problem on GRUB as i told it does "load" windows but right imidietly it crashes

---

### Post by Sef on 2009-05-08
Windows should be on the first primary partition.   That could be part of the problem.

---

### Post by patchido on 2009-05-08
but why can i boot windows if i intern the HD?

---

### Post by patchido on 2009-05-08
well, the problem is still there, ive verified lots of times if i wasnt doing anything wrong, and i dont see it, if i have my primary disc inside my laptop and try to run ubuntu from my ext, it works, if i try to open ubuntu with my exxternal into my laptop as an internal, it works, if i try my windows with my external as an internal it also works, but when i try to open windows from the external conected via USB it goes to windows, and after about 3 secs i get a blue screen of about 2 miliseconds long and system reboots

---

