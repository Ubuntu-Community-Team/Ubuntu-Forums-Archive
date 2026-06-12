---
title: "How to mount sdb &amp; sdc?"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by Magpie. on 2009-09-07
I'm trying to rehabilitate an ancient PC (1999 IBM Aptiva) which somebody gave me. It has three IDE hard-drives, and I've installed Ubuntu 9.04 on the first one. I just assumed that the install process would mount all three, but it didn't, and I can't work out how to mount the other two manually. I'm very new to Linux, by the way.

Fdisk says this:```
[11:40:30 lenb ~]> sudo fdisk -l
[sudo] password for lenb: 

Disk /dev/sda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1638362

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2400    19277968+  83  Linux
/dev/sda2            2401        2491      730957+   5  Extended
/dev/sda5            2401        2491      730926   82  Linux swap / Solaris

Disk /dev/sdb: 13.0 GB, 13030907904 bytes
255 heads, 63 sectors/track, 1584 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e5499

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1584    12723448+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 13.8 GB, 13858725888 bytes
255 heads, 63 sectors/track, 1684 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a36f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1684    13526698+  8e  Linux LVM
[11:40:56 lenb ~]> 
```I know there's data on sdb which should be kept, but sdc is supposed to be empty. There was a version of Linux on this machine long ago and far away. Probably RedHat. And OS2/Warp (RIP), I think. But now it will be 100% Linux.

I've looked in the Pocket Guide and the man pages, but I can't figure it out. Here's what I've tried so far, with no success: [FONT=Courier New][COLOR=RoyalBlue]sudo mount -t fat32 /dev/sdb1 /home/lenb/hdd2 ro[/COLOR][/FONT] but it just lists some command details and does nothing. The directory hdd2 does exist.

I've tried fat32, w95 fat32, and vfat, but no luck. An error message might have helped, but there are none. What next?

[COLOR=Gray][It might be of interest to say that I've tried installing three other distros on this machine without any success at all: PCLinuxOS, SimplyMEPIS, and Mandriva. If Ubuntu hadn't worked OpenSUSE was next in the queue, and then Xandros. But Ubuntu seems fine so far.][/COLOR]

---

### Post by cholericfun on 2009-09-07
go to places and just click on the drives you want to see,

mount via command-line should work though, not an expert myself though

PS, well you want to create that directory youre mounting to first

---

### Post by nothingspecial on 2009-09-07
```
sudo mount -t [COLOR="Red"]vfat[/COLOR] /dev/sdb1 /home/lenb/hdd2
```

---

### Post by wojox on 2009-09-07
Try:

```
sudo mount /dev/sdb1 /mnt
```

---

### Post by nothingspecial on 2009-09-07
Also the ro option you included at the end will mount it read only. Only include that if that is your intention.

---

### Post by anaconda on 2009-09-07
> **nothingspecial said:**
> ```
sudo mount -t [COLOR="Red"]vfat[/COLOR] /dev/sdb1 /home/lenb/hdd2
```

and usually you dont even need to give the "-t vfat" argument, because linux can quess the right filestystem type (I think the default is "-t auto")

But if you mount your disk from terminal then they will be unmounted when you reboot and you will have to manually mount them again.

If you want them to be permanently mounted (remounted each time the computer boots) then you want to add the partitions to yout /etc/fstab file.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by mapes12 on 2009-09-07
You have to mount the drives to folders in your system. This is what I would do:

```
sudo mkdir /sdb
``` ```
sudo mkdir /sdc
```This will make two folders in your Filesystem. Then to mount ```
sudo mount /dev/sdb1 /sdb
``` and to mount the other one ```
sudo mount /dev/sdc1 /sdc
```You can call the folders anything you like. I just called them sdb and sdc for ease of reference. 

Once you have created the folders and mounted the drives to them as above then just click the folder to see the drive contents. Not sure if you need any special applications to view FAT32 content though?

---

### Post by Magpie. on 2009-09-07
Thanks to everybody. 

What Mapes said works fine. "Places" helps too, but doesn't tell me how to do it manually.

(As I did say in my original post, I had already created a target directory, and I had already tried vfat. I still don't know why at least one of my mount attempts didn't work.)

One more question -- how do I make the mounts happen automatically at Boot time? 

Onward, through the fog!

---

