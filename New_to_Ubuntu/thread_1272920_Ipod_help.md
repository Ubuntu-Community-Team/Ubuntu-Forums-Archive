---
title: "Ipod help"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by nicholas mccarthy on 2009-09-22
Hey,

So, I can't get my Ipod Classic to mount anymore. It's the newest one, 120 gbs, and it used to do it on its own, but now it wount mount at all. it says on the ipod that its connected, and on gtkpod, it lists the ipod, and i can go through the ipod, but I can't change anything on the ipod. So any help would be appreciated.

Thanks!

---

### Post by nicholas mccarthy on 2009-09-22
Anything?

---

### Post by j.bell730 on 2009-09-22
Same thing happens to me with my Archos, so I think I'll be able to help you.
Plug your iPod into your computer (and if necessary, set it to USB mode) and go to **Applications** > **Accessories** > **Terminal** and post the output of:
```
sudo fdisk -l
```

---

### Post by nicholas mccarthy on 2009-09-22
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e987

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cb31993

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7301    58645251    7  HPFS/NTFS
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1357     7783940    b  W95 FAT32
Note: sector size is 4096 (not 512)

Disk /dev/sdg: 119.8 GB, 119832539136 bytes
26 heads, 50 sectors/track, 22504 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       22505   117023708    b  W95 FAT32



But yeah, it doesn't even show up anywhere on my computer at all.

---

### Post by j.bell730 on 2009-09-22
Ok, type this in terminal
```
sudo mkdir /media/ipod
sudo mount /dev/sdg1 /media/ipod
```
And if you want to open it to see if it worked, type
```
gksudo nautilus /media/ipod
```

EDIT - Edited first command.

---

### Post by nicholas mccarthy on 2009-09-22
I still can't get it working on any application. it has a folder for the ipod in the Media folder, but not an actual thing where i can mount and unmount it.

---

### Post by j.bell730 on 2009-09-22
> **nicholas mccarthy said:**
> I still can't get it working on any application. it has a folder for the ipod in the Media folder, but not an actual thing where i can mount and unmount it.

Does the ipod folder in the media directory correspond to the contents on your iPod?

---

### Post by nicholas mccarthy on 2009-09-22
Yeah, it does.

---

### Post by j.bell730 on 2009-09-22
Alright, perhaps you need some chmod commands...
```
chmod a+r /media/ipod
chmod a+w /media/ipod
```
Then restart the apps that you are trying to access the iPod on (e.g. GtkPod)

---

### Post by nicholas mccarthy on 2009-09-22
This is what it said for both:

chmod: changing permissions of `/media/ipod': Operation not permitted

---

### Post by j.bell730 on 2009-09-22
> **nicholas mccarthy said:**
> This is what it said for both:

chmod: changing permissions of `/media/ipod': Operation not permitted

```
sudo chmod a+r /media/ipod
sudo chmod a+w /media/ipod
```

---

### Post by nicholas mccarthy on 2009-09-22
Okay, it asked for my password for the first one, then did nothing once i put it in, then i put the second one in and it also did nothing

---

### Post by j.bell730 on 2009-09-22
Just check if you can access your iPod with different applications.

---

### Post by nicholas mccarthy on 2009-09-22
No, still nothing

---

