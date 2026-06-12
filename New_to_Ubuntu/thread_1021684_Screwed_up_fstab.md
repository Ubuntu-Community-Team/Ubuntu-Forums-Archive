---
title: "Screwed up fstab"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by furialis on 2008-12-25
Hi

I edited my fstab file and now the computer will not boot. I made a backup using remastersys and am using that as a live cd. I'm having trouble mounting the drive - I think because it's an encrypted volume.

[php]
b@b:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20e4aa47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c4737

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
b@b:~$ sudo mount /dev/sda1 /hdd2
mount: unknown filesystem type 'crypto_LUKS'
b@b:~$ 
[/php]
Also, I tried to boot into recovery mode but can't edit fstab due to it being read only. Is there a text editor I can use from recovery mode that would allow me to edit that file?

---

### Post by alienexplorers on 2008-12-25
You can boot into recovery mode and when the menu comes up select enter root mode.  Then use nano as the text editor:
> nano /etc/fstab

---

