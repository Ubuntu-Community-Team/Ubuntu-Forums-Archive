---
title: "Ubuntu 9.04 won't boot"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by Trooper511 on 2009-10-07
Need some help with my 9.04 install. I installed ubuntu and had all the updates loaded. I then rebooted to have the take affect and seem to have a conflict with the Acronis OS Selector under my windows install. That prevented windows from booting also. I resolved the Windows issue and that is booting properly but I am unable to get Ubuntu to boot. I have Ubuntu installed on it own drive seperate from the Windows drive. I have booted from the Ubuntu live cd and can view the files on the drive but unable to boot even if I set the bios to boot directly from the Ubuntu drive. I have included the results from the fdisk -l command below and the partition is shown. Any help you can render would be great.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38bec3a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       19456    53882010    5  Extended
/dev/sda5           12749       16572    30716248+   7  HPFS/NTFS
/dev/sda6           16573       18484    15358108+   7  HPFS/NTFS
/dev/sda7           18485       19456     7807558+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38bec3a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       19456    53882010    5  Extended
/dev/sdb5           12749       16572    30716248+   7  HPFS/NTFS
/dev/sdb6           16573       18484    15358108+   7  HPFS/NTFS
/dev/sdb7           18485       19456     7807558+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00071dcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      120850   970727593+  83  Linux
/dev/sdc2          120851      121601     6032407+   5  Extended
/dev/sdc5          120851      121601     6032376   82  Linux swap / Solaris

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9e34a2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       18024   144777748+   7  HPFS/NTFS
/dev/sdd2           18025       36481   148255852+   5  Extended
/dev/sdd5           18025       36481   148255821   bc  Unknown
ubuntu@ubuntu:~$

---

### Post by Zoot7 on 2009-10-07
You could try re-installing grub to the MBR:
**[http://www.sorgonet.com/linux/grubrestore/]("http://www.sorgonet.com/linux/grubrestore/")**

That should get Ubuntu and Windows booting okay but it'll get rid of that Acronis OS selector.

---

### Post by lindsay7 on 2009-10-07
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type “sudo grub”. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Note:  Do not type in the quotation marks in the commands.

---

### Post by yanceypd on 2009-10-07
I recenty updated vista and it wiped out the grub.  Fixing the master boot record fixed it but spooked me real good.  Wonder if MS is try to get rid of us dual booters?

---

### Post by Trooper511 on 2009-10-07
> **lindsay7 said:**
> Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type “sudo grub”. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Note:  Do not type in the quotation marks in the commands.
 
the find returned (hd2,0), when I ran the setup with that, nothing happened, just booted into xp. I then tried the setup (hd0) and now windows will not boot, tried running windows setup to repair the mbr and it crashes with bsod. 

I can see the xp drive from ubuntu so is there a way from ubuntu to fix the mbr so I can get xp back up an running?

---

### Post by lindsay7 on 2009-10-07
See this,

[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

and also,

1.Fix mbr windows xp

[http://pcsupport.about.com/od/termsf/p/fixboot.htm](http://pcsupport.about.com/od/termsf/p/fixboot.htm)
[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by lindsay7 on 2009-10-07
> **Trooper511 said:**
> the find returned (hd2,0), when I ran the setup with that, nothing happened, just booted into xp. I then tried the setup (hd0) and now windows will not boot, tried running windows setup to repair the mbr and it crashes with bsod. 

I can see the xp drive from ubuntu so is there a way from ubuntu to fix the mbr so I can get xp back up an running?


You may want to try this again and try    setup (hd2)

---

### Post by Trooper511 on 2009-10-08
I was able to get Windows back running by breaking my mirror raid array, guess I forgot to mention that, and then was able to run fixmbr and got windows to boot. Could this be my real issue with GRUB, its not recognizing the array and stops? Once I broke the array, grub did run once and I was able to boot to ubuntu but once I did the fixmbr to get xp running it was no more. I will try the setup again on the hd2 with the raid down and see what happens.

---

### Post by LewRockwell on 2009-10-08
> **yanceypd said:**
> I recenty updated vista and it wiped out the grub.  Fixing the master boot record fixed it but spooked me real good.  Wonder if MS is try to get rid of us dual booters?

they sure don't respect their customers and potential customers very much

grub respects previous windows installations...

windows respecting grub...not so much...hahaha...

.

---

### Post by Trooper511 on 2009-10-08
> **lindsay7 said:**
> You may want to try this again and try setup (hd2)
 
Using the setup (hd2) and making this drive the first drive to boot has grub coming up and allows me to boot to both ubuntu and windows, thx for all your help everyone.

---

