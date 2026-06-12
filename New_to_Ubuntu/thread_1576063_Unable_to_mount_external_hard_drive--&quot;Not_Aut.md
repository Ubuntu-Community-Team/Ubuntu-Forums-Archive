---
title: "Unable to mount external hard drive--&quot;Not Authorized&quot;"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by bosco10382 on 2010-09-16
I'm in the process of converting to Ubuntu 10.4 from Windows XP. Experience with Linux<1 week. When I insert either of my external hard drives, and error message appears that says "Not Authorized." This message is simply a bubble that pops up on the desktop, not in terminal. Do I need to create a mount point to use my externals? If so, how?

---

### Post by sandyd on 2010-09-16
> **bosco10382 said:**
> I'm in the process of converting to Ubuntu 10.4 from Windows XP. Experience with Linux<1 week. When I insert either of my external hard drives, and error message appears that says "Not Authorized." This message is simply a bubble that pops up on the desktop, not in terminal. Do I need to create a mount point to use my externals? If so, how?
plug in the external drive and post the output of
```

sudo fdisk -l
```

---

### Post by sandyd on 2010-09-16
and post the output of
```

groups
```

---

### Post by mapman88 on 2010-09-18
I have the same issue; I copied my windows files to a new external HD, then I loaded ubuntu 10.04 (dual boot) which I have been using. I would like to access the external drive to get at my windows files (mainly photos and music, perhaps a few documents) so I can reload Ubuntu and get rid of XP altogether,

Sorry, don't mean to hijack the thread, let me know if I should buzz off.

sudo fdisk - l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf211f211

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29268   235095178+   7  HPFS/NTFS
/dev/sda2           29270       30401     9092790    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd523cc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15234   122362774+   7  HPFS/NTFS
/dev/sdb2           15234       30402   121835521    5  Extended
/dev/sdb5           15234       29780   116841472   83  Linux
/dev/sdb6           29780       30402     4993024   82  Linux swap / Solaris

Groups,

steve adm dialout fax cdrom floppy tape audio dip video plugdev fuse lpadmin netdev admin sambashare

---

### Post by garvinrick4 on 2010-09-18
If your second drive is the external drive mapman88.
Put in a Ubuntu cd and boot off of it and open a terminal:
```
sudo mkdir /media/root
``````
sudo mount /dev/sdb5 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sdb
``````
sudo umount /media/root
```Boot into your USB drive in BIOS either set before HDD in BIOS or choose at boot in Bios.
```
sudo update-grub
```Should now be able to mount sdb1 your Windows install when you boot Ubuntu on sdb on external drive
and or boot into it thru grub2 in boot menu.

---

### Post by mapman88 on 2010-09-18
Ya Know, my computer (HP Media Center) has two 250 GB hard drives, and I think sdb1 is one of them. Is that perhaps why I don't see sda1 on my fdisk-l search?

oh, sorry bout that, sda1 is there on my fdisk-l.

---

### Post by mapman88 on 2010-09-18
It looks like sudo fdisk -l is not seeing my WD Smart Drive, just my two 250 GB hard drives. Is that correct?  I believe the icon forthe WD Smart Drive was on my ubuntu desktop recently, but is not any longer. I will move WD Smart Drive to a Vista laptop I have and see what gives there.

---

### Post by cmcanulty on 2010-09-18
If you didn't safely remove it before ,hook it to a windows machine and safely remove then be sure to unmount it thereafter. Windows seems more forgiving on that issue.

---

### Post by sandyd on 2010-09-18
> **mapman88 said:**
> I have the same issue; I copied my windows files to a new external HD, then I loaded ubuntu 10.04 (dual boot) which I have been using. I would like to access the external drive to get at my windows files (mainly photos and music, perhaps a few documents) so I can reload Ubuntu and get rid of XP altogether,

Sorry, don't mean to hijack the thread, let me know if I should buzz off.

sudo fdisk - l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf211f211

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29268   235095178+   7  HPFS/NTFS
/dev/sda2           29270       30401     9092790    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd523cc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15234   122362774+   7  HPFS/NTFS
/dev/sdb2           15234       30402   121835521    5  Extended
/dev/sdb5           15234       29780   116841472   83  Linux
/dev/sdb6           29780       30402     4993024   82  Linux swap / Solaris

Groups,

steve adm dialout fax cdrom floppy tape audio dip video plugdev fuse lpadmin netdev admin sambashare
lemme cheat and allow you to mount any disk......
```

sudo usermod -a -G disk *your_username_here*
```

---

### Post by garvinrick4 on 2010-09-18
I  thought he wanted to boot from sdb instead of just  mount and read/write.
Still do not know.
Oh well either will work I guess to mount. Never used post 9's but if it works it works. Nice to learn
new things everyday.

---

### Post by mapman88 on 2010-09-18
OK, and this might help bosco10382 as well, I booted to XP, accessed my WD Smart Drive with Smartware, shut down XP and booted to Ubuntu Lynx, and the Smart Drive was mounted automatically. Now my issue is, in *Ubuntu, can I access the data I backed up in XP on this drive?, It requires me to run unlock.exe, which I can't do in UBuntu, can I?

---

### Post by mapman88 on 2010-09-18
Sorry for the confusion, People. Not the first time I did not make myself clear. And I have found I can read my backed up files while in Ubuntu, which is what I was up to in the beginning. 

thanks again

---

### Post by garvinrick4 on 2010-09-18
> **mapman88 said:**
> Sorry for the confusion, People. Not the first time I did not make myself clear. And I have found I can read my backed up files while in Ubuntu, which is what I was up to in the beginning. 

thanks againLinux can read/write to NTFS or FAT so I would have to quess that maybe you should make sure your Folders in Windows you want to access should be marked shared in Windows and read write I think windows asks for.

---

### Post by 32ftpersecond on 2010-12-15
Hey everyone,

I've been really patiently attempting to go over these steps; however, I'm still unable to access an external hard-drive of mine after merely plugging it in to a windows machine to listen to an mp3 - I have had this external harddrive for 2+years, no problems, I only run Ubuntu but I have definitely plugged into OS X and Windows in the past and not received this error:

> Unable to mount Lokaler Datenträger
Error mounting: mount exited with exit code 2: 

As for some pedigree info:

> 
sean@socrates:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008c555

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18693   150145024   83  Linux
/dev/sda2           18693       19458     6142977    5  Extended
/dev/sda5           18693       19458     6142976   82  Linux swap / Solaris

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc390fdc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       12161    97683201    7  HPFS/NTFS
sean@socrates:~$ sudo usermod -a -G disk sean
sean@socrates:~$ groups
sean adm dialout cdrom plugdev lpadmin admin sambashare

If anyone has any more suggestions I would gladly hear them.

Thanks

---

