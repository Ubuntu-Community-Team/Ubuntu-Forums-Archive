---
title: "Need help to repair or reinstall ubuntu 10.04."
date: 2010-10-16
forum: New to Ubuntu
---

### Post by ivarn on 2010-10-16
Hey. I am daul booting ubuntu 10.04 and windows 7 on my pc.
Yesterday I got a new kernel after a system update and everything went wrong.
I can't open ubuntu from any of the kernel and the recovery modes doesn't work either.
When I try to boot ubuntu I get this error:
 
[ 2.496925] [drm] mouveau 0000:03:00.0: 0x1191: parsing clock script 0. [ 2.498069] console: switching to colour frame buffer device 170x48.
Init: failed to spawn ufw pre-start process: unable to execute: no such file or directory.
 
And it says something about Bryptdisk, rc-sysinit and pvymouth as well whatever that means.
So now I need to know, how can I fix this problem or reinstall ubuntu?
I tried to use the live cd but it will only let me install ubuntu side by side, or I will have to remove windows in the process, and I don't wanna remove windows.
Please help me.

---

### Post by Bob Bertrands on 2010-10-16
If you use the live-cd: There is an advanced option when choosing where to install ubuntu. It reads something like manually chose partition or make new partition table. when you select this and select the ext4 partition (that's the one you installen ubuntu on) ubuntu will be install on this partition and your problem will probably be solved.

B

---

### Post by ivarn on 2010-10-16
> **Bob Bertrands said:**
> If you use the live-cd: There is an advanced option when choosing where to install ubuntu. It reads something like manually chose partition or make new partition table. when you select this and select the ext4 partition (that's the one you installen ubuntu on) ubuntu will be install on this partition and your problem will probably be solved.

B

Ok I tried but no luck. It wouldn't let me. it said I have to choose a root filesystem or something. I thought the ex was the filesystem.t

---

### Post by JamButty on 2010-10-16
Maybe others have ideas on how to repair, but if you want to wipe the Linux partitions and reinstall (you don't mind losing your files on the Linux side), you can do that from the install media (CD "live-disk").  I got similar errors when trying to install to a specified partition when I initially installed. After many frustrating attempts, I dropped that and let the installation disk sort out the partitions (side by side option).
Boot to the install disk, (the "try" option) use system->administration->disk utility
That should give information on the left side and a graphic representation at the bottom right, showing the media available to your machine. If you choose your hard disk on the left side, the graphic will show you your partitions. There will be one (at least) in NTFS format for your WIN7 and  1 (at least) for your Linux in ext3 or ext4 format and a swap partition (usually 1-5 GB).
If you select a partition in the GUI, you can delete it directly. Deleting your Linux partitions will free that space and simplify reinstallation. Once those are gone, you can reboot to the live-disk and install with the side-by-side option. This will NOT remove your Win7 installation. You just need to be very careful about which partitions you are deleting.

This is a bit extreme though and you would lose any data on the Linux side, so it might be worth waiting a day for any other replies on how to repair without reinstallation.

---

