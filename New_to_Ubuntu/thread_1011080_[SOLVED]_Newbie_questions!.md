---
title: "[SOLVED] Newbie questions!"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by timtom1 on 2008-12-14
I have a EEE PC 901 with a 4gb drive with Ubuntu on it and a second SSD which is 16gb.

I have my windows XP Cd but it isn't service pack 2 can that be installed on the second 16gb drive?

I try to input an SD card which is FAT32 but I get Cannot mount volume 'TIM' Mount: must be superuser to use mount I did a bit of searching and I tired to mount it in sudo but its not working

```
sudo mount -t auto /dev/sdd1 /media/tim
```

---

### Post by HermanAB on 2008-12-14
The /media directory is used by auto-mounting software to mount removable media.

if you want to manually mount something, then you should do so in the /mnt directory.  To do a manual mount, you need to create the mount point yourself first:
sudo mkdir /mnt/wherever
sudo mount /dev/whatever /mnt/wherever

Cheers,

Herman

---

### Post by Catalyst2Death on 2008-12-14
> **HermanAB said:**
> The /media directory is used by auto-mounting software to mount removable media.

if you want to manually mount something, then you should do so in the /mnt directory.  To do a manual mount, you need to create the mount point yourself first:
sudo mkdir /mnt/wherever
sudo mount /dev/whatever /mnt/wherever

Cheers,

Herman

I didn't know that /mnt/ was for user mounting purposes (I'll use it from now on though)... I always mounted into /media/ and it didn't affect things...  

As for the OP's questions:

You want to install XP on a secondary SSD after installing ubuntu on the 4gb partition?  You should be able to.  It may go something like this (someone with more experience should correct me if I'm wrong):

Boot the XP cd and install it on the 16gb media.  Then if XP doesn't flag the partition bootable, you should still restart into Ubuntu.  If it does mark it bootable, you'll automatically boot into XP.  If this happens, you put the Ubuntu LiveCD in and boot to that.  Then you use gParted to mark the ubuntu partition bootable and then restart.  It should go into ubuntu. This link: [http://novex.blogspot.com/2007/05/how-to-dual-boot-linux-and-windows-xp.html](http://novex.blogspot.com/2007/05/how-to-dual-boot-linux-and-windows-xp.html) will walk you through boot flags in ubuntu.  It may also help with the whole process.  Then you need to edit your grub to find the XP bootloader...

All you need to do is point grub to the second disk which contains xp and use the chainloader option.  It should look something like this when your done:
```

title=Windows
root (hd1,0)
rootnoverify (hd1)
chainloader +1
```

For further reading:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://www.linuxforums.org/forum/peripherals-hardware/10300-configuring-grub-windows.html](http://www.linuxforums.org/forum/peripherals-hardware/10300-configuring-grub-windows.html)
[http://novex.blogspot.com/2007/05/how-to-dual-boot-linux-and-windows-xp.html](http://novex.blogspot.com/2007/05/how-to-dual-boot-linux-and-windows-xp.html)

---

### Post by northern lights on 2008-12-14
> **timtom1 said:**
> I have my windows XP Cd but it isn't service pack 2 can that be installed on the second 16gb drive?[/CODE]
Theoretically yes.

However you will encounter a few solvable problems on the way.

Windows, regardless of what version, wants to reside on the first partition of the first drive. So you'll have to [remap]("http://www.gnu.org/software/grub/manual/html_node/map.html") partitions before chainloading NTLDR (Windows bootloader) from GRUB.

And further, when installing, Windows will inevitably rewrite the MBR and thus you'd have to [restore GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") after installing, otherwise you won't be able to boot Ubuntu.

---

### Post by timtom1 on 2008-12-14
Thanks for the quick replies

I made a directory called windows

When I try ```
sudo mount /dev/TIM /mnt/windows
```

I get ```
sudo mount /dev/TIM 
```not found?

---

### Post by albinootje on 2008-12-14
> I get
> Code:
>
> sudo mount /dev/TIM
>
> not found? 

You should find out which device file descriptor your SD card is using.
On my netbook i have to put the SD card in before booting.

Is it /dev/sdd1 like you've used before ?
I thought the SD-cards usually used something like /dev/mmcblk0p1
(I saw it on my netbook before).

You can check this with : dmesg|grep mm
to see whether it is indeed /dev/mmcblk0p1 or the like.

---

### Post by timtom1 on 2008-12-14
ok I am confused sorry!:confused:

Starting from scratch.

I have my SD card in before I boot I still get 

Unable to mount volume 'TIM'

"Mount: must be superuser to use mount"

in the terminal what sudo code would I use to mount it?

the SD card is Called TIM

---

### Post by albinootje on 2008-12-14
Can you try this : 
sudo mount /dev/mmcblk0p1 /mnt/windows

---

### Post by timtom1 on 2008-12-14
just made a windows directory under /mnt/

now i get 

mount: special device /dev/mmcblk0p1 does not exist

---

### Post by albinootje on 2008-12-14
Okay, we're making some progress :)

Can you please post the output of :
dmesg|grep mm

and :
dmesg|grep sd

---

### Post by rlunger on 2008-12-14
You mentioned earlier that you tried to mount /dev/sdd1.  Where did you get this device name from?  If sdd1 is correct, then use:

    sudo mount -t vfat /dev/sdd1 /mnt/windows

'-t vfat' tells Linux that the partition on /dev/sdd1 is a FAT12/16/32 filesystem.  You cannot mount /dev/TIM directly because 'TIM' is not a device or partition consistent with Linux naming schemes (i.e., sda1, hda1, etc.).  You may be able to find 'TIM' in /dev/disk/by-label/.  

Hope this helps.  BTW, it doesn't really matter if you choose to mount a filesystem in /media or /mnt.  Linux will automount removable media in /media, but you can manually mount a partition wherever you choose.

---

### Post by timtom1 on 2008-12-14
tim@ubuntu-laptop:~$ sudo dmesg|grep mm
[    0.000000] Linux version 2.6.24-21-eeepc (root@adamm-laptop) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Aug 7 22:18:05 MDT 2008 (Ubuntu 2.6.24-4.6-eeepc)
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Kernel command line: root=UUID=5165c303-be70-4ea4-9657-955cf3e42198 ro quiet splash
[   20.354651] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   20.968604] mice: PS/2 mouse device common for all mice
[   24.330704] kjournald starting.  Commit interval 5 seconds
[  250.841264] kjournald starting.  Commit interval 5 seconds
tim@ubuntu-laptop:~$ 
tim@ubuntu-laptop:~$ 
tim@ubuntu-laptop:~$ sudo dmesg|grep sd
[   23.919691] Driver 'sd' needs updating - please use bus_type methods
[   23.919868] sd 1:0:0:0: [sda] 7880544 512-byte hardware sectors (4035 MB)
[   23.919904] sd 1:0:0:0: [sda] Write Protect is off
[   23.919912] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.919969] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   23.920078] sd 1:0:0:0: [sda] 7880544 512-byte hardware sectors (4035 MB)
[   23.920110] sd 1:0:0:0: [sda] Write Protect is off
[   23.920118] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.920174] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   23.920184]  sda: sda1 sda2 < sda5 >
[   23.922205] sd 1:0:0:0: [sda] Attached SCSI disk
[   23.922352] sd 1:0:1:0: [sdb] 31522176 512-byte hardware sectors (16139 MB)
[   23.922387] sd 1:0:1:0: [sdb] Write Protect is off
[   23.922395] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   23.922451] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   23.922558] sd 1:0:1:0: [sdb] 31522176 512-byte hardware sectors (16139 MB)
[   23.922587] sd 1:0:1:0: [sdb] Write Protect is off
[   23.922594] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   23.922652] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   23.922662]  sdb: sdb1
[   23.924160] sd 1:0:1:0: [sdb] Attached SCSI disk
[   23.934907] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   23.934957] sd 1:0:1:0: Attached scsi generic sg1 type 0
[   29.800330] sd 2:0:0:0: [sdc] 1984000 512-byte hardware sectors (1016 MB)
[   29.801210] sd 2:0:0:0: [sdc] Write Protect is on
[   29.801220] sd 2:0:0:0: [sdc] Mode Sense: 03 00 80 00
[   29.801225] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   29.803964] sd 2:0:0:0: [sdc] 1984000 512-byte hardware sectors (1016 MB)
[   29.804875] sd 2:0:0:0: [sdc] Write Protect is on
[   29.804884] sd 2:0:0:0: [sdc] Mode Sense: 03 00 80 00
[   29.804890] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   29.804900]  sdc: sdc1
[   29.806375] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   29.806481] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   34.274589] Adding 224868k swap on /dev/sda5.  Priority:-1 extents:1 across:224868k
[   34.889618] EXT3 FS on sda1, internal journal
[   38.386111] audit(1229281550.419:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4853 profile="/usr/sbin/cupsd" namespace="default"
[  250.849617] EXT3 FS on sdb1, internal journal
tim@ubuntu-laptop:~$

---

### Post by timtom1 on 2008-12-14
the answer was sdc1 

sudo mount /dev/sdc1 /mnt/windows

thank you so much everybody that has helped me, how do I close this post as complete? SOLVED

---

### Post by albinootje on 2008-12-14
Cool! :)

To add [Solved] ->
[http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

