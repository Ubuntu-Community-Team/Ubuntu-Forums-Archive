---
title: "Ubuntu 9.10//XP//problem grub bootloader"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by Suranjandeo on 2010-08-07
Hi friends,
regards.

I installed windows XP2 with 4 partition on harddisk.
Then with ubuntu live CD Gparted deleted one partition and made it unallocated and install ubuntu 9.10 there.

Since then grub bootloader problem is there.
The initial option to choose OS is there. When i select Linux then i can enter in it. But when i choose windows XP then following error message is coming---

"error : invalid signature"

when i press any key then it returns to menu. when i select XP and press "e" then message comes...

"insmod ntfs 
drivemap -s (hd0) ${root}
chain loader +1"

Then according to one tutorial
 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) 

i booted with windows XP CD and repaired it with "fixboot" and "fixmbr".

Then it worked. winXP is working but grub menu is not there to choose OS. It directly opens winXP. no trace of ubuntu.

Then to recover grub i booted with live ubuntu cd and ran in terminal 

"sudo mkdir /media/sda7
sudo mount /dev/sda7 /media/sda7"

and then

"sudo grub-install --root-directory=/media/sda7 /dev/sda"

And it worked. Grub menu is there to select OS. I can access ubuntu but not XP. Xp's probblem returns back what i described above.

point is that i can get only one OS either ubuntu or win. Pls help b/c i want and i need both OS.

with regards
suranjan

---

### Post by Ozymandias_117 on 2010-08-07
> **Suranjandeo said:**
> Hi friends,
regards.

I installed windows XP2 with 4 partition on harddisk.
Then with ubuntu live CD Gparted deleted one partition and made it unallocated and install ubuntu 9.10 there.

Since then grub bootloader problem is there.
The initial option to choose OS is there. When i select Linux then i can enter in it. But when i choose windows XP then following error message is coming---

"error : invalid signature"

when i press any key then it returns to menu. when i select XP and press "e" then message comes...

"insmod ntfs 
drivemap -s (hd0) ${root}
chain loader +1"

Then according to one tutorial
 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) 

i booted with windows XP CD and repaired it with "fixboot" and "fixmbr".

Then it worked. winXP is working but grub menu is not there to choose OS. It directly opens winXP. no trace of ubuntu.

Then to recover grub i booted with live ubuntu cd and ran in terminal 

"sudo mkdir /media/sda7
sudo mount /dev/sda5 /media/sda7"

and then

"sudo grub-install --root-directory=/media/sda7 /dev/sda"

And it worked. Grub menu is there to select OS. I can access ubuntu but not XP. Xp's probblem returns back what i described above.

point is that i can get only one OS either ubuntu or win. Pls help b/c i want and i need both OS.

with regards
suranjan

Boot to the Windows CD and ONLY do FIXBOOT. This will not overwrite GRUB.

---

### Post by Suranjandeo on 2010-08-07
> **Ozymandias_117 said:**
> Boot to the Windows CD and ONLY do FIXBOOT. This will not overwrite GRUB.

Thank you for your kind reply.
According to your suggestion i did boot with the windows CD and only did FIXBOOT. 

But it didn't do anything. No changes happened. Nothing happened. When i exit from windows boot Cd and computer started then initial grub menu appeared where i could choose OS. I chose WinXP but same error message came "invalid signature" what i have described in my first letter in detail. 

After doing "fixboot" only i can access ubuntu as i could before doing it. Actually doing only "fixboot" showed no effect on either OS.

Waiting for help 
with regards...
Suranjan

---

### Post by Suranjandeo on 2010-08-07
> **Suranjandeo said:**
> Hi friends,
regards.

I installed windows XP2 with 4 partition on harddisk.
Then with ubuntu live CD Gparted deleted one partition and made it unallocated and install ubuntu 9.10 there.

Since then grub bootloader problem is there.
The initial option to choose OS is there. When i select Linux then i can enter in it. But when i choose windows XP then following error message is coming---

"error : invalid signature"

when i press any key then it returns to menu. when i select XP and press "e" then message comes...

"insmod ntfs 
drivemap -s (hd0) ${root}
chain loader +1"

Then according to one tutorial
 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) 

i booted with windows XP CD and repaired it with "fixboot" and "fixmbr".

Then it worked. winXP is working but grub menu is not there to choose OS. It directly opens winXP. no trace of ubuntu.

Then to recover grub i booted with live ubuntu cd and ran in terminal 

"sudo mkdir /media/sda7
sudo mount /dev/sda5 /media/sda7"

and then

"sudo grub-install --root-directory=/media/sda7 /dev/sda"

And it worked. Grub menu is there to select OS. I can access ubuntu but not XP. Xp's probblem returns back what i described above.

point is that i can get only one OS either ubuntu or win. Pls help b/c i want and i need both OS.

with regards
suranjan

Hi there,
I ran in terminal "sudo fdisk -l" and here is the report. Someone might need to see it. It might help to fix problem.

baba@baba:~$ sudo fdisk -l
[sudo] password for baba: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003309a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/sda2            4845       19457   117378922+   f  W95 Ext'd (LBA)
/dev/sda5            4845        9688    38909398+   e  W95 FAT16 (LBA)
/dev/sda6            9689       14532    38909398+   e  W95 FAT16 (LBA)
/dev/sda7           14533       19272    38074018+  83  Linux
/dev/sda8           19273       19457     1485981   82  Linux swap / Solaris
baba@baba:~$ 

Pls help 
waiting...
suranjandeo

---

### Post by oldfred on 2010-08-07
Once you ran the fixmbr command you wrote the windows boot loader to the MBR. You just need to reinstall grub or grub2 to the MBR. Just be sure to install the correct version of grub. You have grub2 if you did a new install of 9.10. If you upgraded from an older version of Ubuntu you may still have grub legacy.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install MBR from LiveCD, Ubuntu install on sda7 and want grub2 in drive sda's MBR:
Find linux partition, change sda7 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
(confirm sda7 is linux partition which it looks like from your list)
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by Suranjandeo on 2010-08-07
> **oldfred said:**
> Once you ran the fixmbr command you wrote the windows boot loader to the MBR. You just need to reinstall grub or grub2 to the MBR. Just be sure to install the correct version of grub. You have grub2 if you did a new install of 9.10. If you upgraded from an older version of Ubuntu you may still have grub legacy.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install MBR from LiveCD, Ubuntu install on sda7 and want grub2 in drive sda's MBR:
Find linux partition, change sda7 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
(confirm sda7 is linux partition which it looks like from your list)
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Respected brother,
I followed your suggestion. But error message came.
I boot with live CD. went in terminal and typed-sudo mount /dev/sda7 /mnt 
then following error message came----

"wrong fs type, bad option, bad super block on /dev/sda7, missing codepage or helper programme or other error."

Sda7 is my linux. And sda1 is windows XP.
Now i am in Ubuntu and it is working fine. But to enter in winXP i have to put live CD and run fixmbr again. After run fixmbr i can access winxp normally, no problem as many times as i can. But when once i put ub untu live CD and install grub by the way i have discribed in my first letter then i can access ubuntu but not XP.

Problem....:(
waiting for further reply..
suranjan

---

### Post by bildr on 2010-08-07
I'm not sure how some folks have all these MBR problems.  My install always just worked except for some install from usb funniness.  If you install from CD, no problems.  Check your grub settings and boot.ini inside of windows partition.  boot.ini is the source of many dual boot woes.  invalid signature is issued by grub or windows?

---

### Post by oldfred on 2010-08-07
Do you still get the bad superblock error? or does grub2 just install ok.

From Ubuntu if you run this does it find your windows?

sudo upate-grub

---

### Post by Suranjandeo on 2010-08-07
[QUOTE=oldfred;9691709]Do you still get the bad superblock error? or does grub2 just install ok.

From Ubuntu if you run this does it find your windows?

sudo upate-grub[/QUOTE

 Internet server had some problem that's why it is my late reply. Sorry.

YEs still i have the bad superblock error. grub2 didn't install. It has still error messaage.

I ran in terminal of Ubuntu "update-grub" but nothing happened. It shows result that is showing winxp on sda1 but when i choose xp at initial grub menu then same error message is coming- "invalid signature".

waiting...
suranjan

---

### Post by oldfred on 2010-08-07
Possible fixes for superblock error:

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

---

### Post by Suranjandeo on 2010-08-07
> **oldfred said:**
> Possible fixes for superblock error:

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

thank you. Now i will check all these threads and then inform you. thank you again.

With regards...
suranjan

---

