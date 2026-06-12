---
title: "Memory Stick"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by soltero5965 on 2010-08-01
Hello i am using lucid on my sony vaio vgn nr 430d for some time now and i just noticed that when i insert my memory stick pro duo and my sd memory card they are not read and not mounted.
My cd/dvd and usb drive have no issue 
What could be wrong?
Help....Thanks

---

### Post by beew on 2010-08-01
Go to "Places", open any directory there (say, "Music") Click "Edit" and choose "Preference" in the dropdown menu and then go to "Media" to set your autoplay options.

---

### Post by soltero5965 on 2010-08-01
> **beew said:**
> Go to "Places", open any directory there (say, "Music") Click "Edit" and choose "Preference" in the dropdown menu and then go to "Media" to set your autoplay options.

Tried it didn't work... 
Anybody...

---

### Post by skatinjj on 2010-08-01
Just got back into Ubuntu after about a year, but this shouldn't be too hard.

Open a terminal and enter:

```
sudo fdisk -l
```

It will ask for your password, enter it and hit enter (will not display anything while typing the password, that is normal).

There will be a list of drives there like sda,sda1, etc. for as many drives as you have hooked up.

The first flash drive is probably sdb and the second sdb1.

If those are listed, you can run this command to mount them:

```
sudo mount /dev/sdb /media/name_of_device
```

Replace name_of_device with what you want to refer to it as.

---

### Post by soltero5965 on 2010-08-01
> **skatinjj said:**
> Just got back into Ubuntu after about a year, but this shouldn't be too hard.

Open a terminal and enter:

```
sudo fdisk -l
```It will ask for your password, enter it and hit enter (will not display anything while typing the password, that is normal).

There will be a list of drives there like sda,sda1, etc. for as many drives as you have hooked up.

The first flash drive is probably sdb and the second sdb1.

If those are listed, you can run this command to mount them:

```
sudo mount /dev/sdb /media/name_of_device
```Replace name_of_device with what you want to refer to it as.
Hello this is  what i have ...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d409e10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1142        8662    60402017    7  HPFS/NTFS
/dev/sda2            8662       19458    86715393    5  Extended
/dev/sda5            8662       19013    83141632   83  Linux
/dev/sda6           19013       19458     3572736   82  Linux swap / Solaris


no sdb o sdb1 and actually it's mot only my memory stick but also my sd card reader which don't work and not mounted..what could be the problem

---

