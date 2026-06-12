---
title: "load grub for 10.04 lucid lynx"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by utkarshjadhav on 2010-08-24
I had installed 10.04 on one of the drives in hard-disk.other was windows XP.
Due to some reasons I had to remove windows and again install it.
In order to recover the ubuntu,I used auto grub loader.
But it isnt working...
Plz help me through this in order to get ubuntu back.
Should I use the ubuntu10.04 cd????

---

### Post by utkarshjadhav on 2010-08-24
@ grub-
fix of boot failed

use:
      Use normal super grub disk
      rescatux (comming soon or later)
      linux live cd 
      the force ,luke.

---

### Post by LiquidMeson on 2010-08-24
pop in the live ubuntu disk. 

alt-f2 palimpsest
then in terminal
sudo grub-install (ubuntu location ex. /dev/sda)
sudo update-grub
reboot

---

### Post by utkarshjadhav on 2010-08-25
DID THE FOLLOWING   
               1.pop in the live ubuntu disk.
alt-f2 palimpsest
then in terminal
      2. sudo grub-install /dev/sda
[B]
/usr/sbin/grub-probe :error: cannot find a device for /boot/grub(is /dev mounted?)
[/B]



after palimpsest--
in the hard disk option--
there are two options-
one with DRIVE and other below it Volumes..
in DRIVE--
DEVICE:/dev/sda

in volume:
Device:/dev/sda1
(with option for mounting )
i did mount it ..
and checked for 

sudo grub-install /dev/sda1
[B]/usr/sbin/grub-probe :error: cannot find a device for /boot/grub(is /dev mounted?)




*****
[/B]wont auto disk loader( a software i guess) help???
I am novice for  grub loading ...
plz help me...

---

### Post by arpanaut on 2010-08-25
From the terminal post the output of:

```
sudo fdisk -l
```

That is a small L not a one

Was your Ubuntu install on separate partition, or within windows via wubi?

---

### Post by utkarshjadhav on 2010-08-26
output for the   sudo fdisk -l
```

Disk /dev/sda:160.0GB ,160041885696 bytes
255heads,63 sectors/track,19457 cylinders
units=cylinders of 16065*512=8225280 bytes
Sector size (logical/physical):512 bytes/512 bytes
I/O size (minimum/optimal):512 bytes/512 bytes
Disk identifier:0X41ab2316
Device        boot     Start        End            Blocks            Id              System
/dev/sda                   1             11            88326           de              Dell Utility
/dev/sda2   *           12             6385         51199155       7              HPFS/NTFS
/dev/sda3                 6386         19458       105002505      f             W95 Ext'd (LBA)
partition 3 does not end on cylinder boundary.
/dev/sda5                 6386         12759         51199123+     7           HPFS/NTFS
/dev/sda6                12760         13987        9858048         83          Linux
/dev/sda7                 13987        19093        41014272        83         Linux
/dev/sda8                 19093         19458        2928640         82       Linux swap/solaries

```

On my LAPTOP-
I had windows XP SP2.Then I installed 10.04 on SEPARATE drive.(by creating free space etc etc ..)
after that removed XP and installed it again...
now grub is missing and ubuntu cant be opened .

---

### Post by wojox on 2010-08-26
So now you just need to [Reinstall from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by utkarshjadhav on 2010-08-26
@reinstall:
reinstalling wont affect my  data in ubuntu,will it??

I am not in mood to  install many packages all again.... :( :(

---

### Post by utkarshjadhav on 2010-08-27
I installed grub successfully by
sudo apt-get install grub


for the command---
sudo grub-setup -d /media/XXXX/boot/grub /dev/sda


It shows grub-setup ---invalid command...



And none of the method is working.... :(:(:(

---

### Post by utkarshjadhav on 2010-08-27
[B][COLOR=Navy][SIZE=3]did with the following steps---

Reinstalling GRUB 2 from LiveCD[/SIZE][/COLOR] [/B]
If you cannot boot from GRUB 2 and need to reinstall it, here is the  simple method. For more details or for advanced options, refer to the  Ubuntu community documentation here: [Grub2 - Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"):
[LIST]
[*]Boot the Karmic or Lucid LiveCD (Try without installing).
[*]From the Desktop, open a terminal - Applications, Accessories, Terminal.
[*]Determine your normal system partition - `sudo fdisk -l`  (That is a lowercase L)
[*]If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
[*]Mount your normal system partition:      Code:
     sudo mount /dev/sdXY /mnt
[LIST]
[*]Example: sudo mount /dev/sd*a1* /mnt
[*]Note: The partition to mount is normally the partition on which  Ubuntu was installed: sda1, sdb5, etc. If you have a separate /boot  partition, use the device on which the /boot partition is located. Grub 2  works best when installed in the MBR of the drive to which BIOS boots.  Also remember that you *mount* the partition (including the number) in this step, but you do *not* include the partition number when you run the "sudo grub-install" command later.
[*]Note: GRUB 2 counts the first drive (X) as "0", but the first partition (Y) as "1"
[/LIST]
 
[*]Only if you have a separate boot partition:
[LIST]
[*]     Code:
     sudo mount /dev/sdXY /mnt/boot 
 with sdXY being your /boot partition designation.
[/LIST]
 
[*]Reinstall GRUB 2:      Code:
     sudo grub-install --root-directory=/mnt /dev/sdX
[*]
[LIST]
[*]Example: sudo grub-install --root-directory=/mnt /dev/sd*a*
[*]Note: Substitute the device on which Ubuntu was installed - sda, sdb, etc. Do *not* specify a partition number.
[/LIST]
 
[*]Unmount the partition *:       Code:
     sudo umount /mnt
[*]Reboot.




-------------------------------------------------------------------------------------

----------------------------------------------------------------------------------

[U][B][COLOR=Red]now when the PC reboots grub opens...
LOL ...then what to do ...It doesnt provide me options like ubuntu,XP....

As told earlier I am novice for gurb loading thing...help....[/COLOR][COLOR=Red]
I mean how to load menus in grub...?????[/COLOR][/B][/U]
[/LIST]

---

### Post by 29732 on 2010-08-27
what about installing burg?
it is similar, just a tiny bit different 
[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

---

### Post by utkarshjadhav on 2010-08-27
thanx for that....:D






But finally I ended up installing both OS XP and ubuntu lucid once again...
though the grub was loaded my problem wasnt solved...

---

