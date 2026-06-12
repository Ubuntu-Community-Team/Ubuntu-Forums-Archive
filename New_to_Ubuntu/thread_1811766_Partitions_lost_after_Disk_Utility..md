---
title: "Partitions lost after Disk Utility."
date: 2011-07-25
forum: New to Ubuntu
---

### Post by MG&amp;TL on 2011-07-25
I have dual-booted Ubuntu 11.04 with Windows 7, but then tried ku-, xu-, and lu- buntus, and accidentally Fedora (just don't ask!), choosing 'replace ubuntu' every time. I then re-installed Ubuntu.

However, I was confused as to why I now had less hard disk space on the Ubuntu partition than the Windows one.

So I used 'disk utility' to see what was taking the room, and it turns out I have **FIVE** separate 'swap' partitions, each of them 4GB or thereabouts. I have 4GB RAM, so what's it up to and how do I cure it?

---

### Post by Elfy on 2011-07-25
Can I assume that you now only have one linux install? 

Basically what you can do is check which swap is being used.

```
cat /etc/fstab |grep swap
```

Note the UUID.

Boot a live cd, from a terminal run ```
sudo blkid
``` to find which swap you need to keep, start gparted, right click on swaps which are being used and swapoff.

Delete the unused swaps. 

If you have more than one linux install - do that still - but you'll need to check each fstab and edit their swap's.

What happened is that (I assume) you used the autoinstaller - it would create / and swap.

Edit - if you are unsure when in the livecd please run 

```
sudo fdisk -l
sudo blkid
```

and tell us what the UUID was from fstab.

---

### Post by MG&amp;TL on 2011-07-25
Yep, I used the Ubuntu installer. I CAN use the manual one, it's just much easier not to.

I did try to delete them in Disk Utility, one or two went, but the rest said they were in use. Hmmm.

cat /etc/fstab command returns:


```
# swap was on /dev/sda10 during installation
UUID=1b209c35-eec4-4bed-a54e-feea11bd3232 none            swap    sw              0       0

```

And I want the UUID bit. OK, so once I've done this I'll be able to use the memory they took up?

---

### Post by Elfy on 2011-07-25
Can you post the result of this from your install rather than boot the livecd.

```
sudo blkid
sudo fdisk -l
mount
```

You 'might' be able to do this without using the livecd.

Edit - if you booted it already then nevermind :)

---

### Post by MG&amp;TL on 2011-07-25
Nope, not yet, got to find the blinking thing first. :p

sudo blkid:


```
/dev/sda1: LABEL="Recovery" UUID="C8AA06B5AA069FD4" TYPE="ntfs" 
/dev/sda2: LABEL="System Reserved" UUID="8A301D04301CF8C1" TYPE="ntfs" 
/dev/sda3: UUID="38921F23921EE562" TYPE="ntfs" 
/dev/sda5: UUID="c570ce31-e22f-43d6-bc99-f93b0505f38b" TYPE="swap" 
/dev/sda6: UUID="2c685e84-3120-496f-ab18-e5f26ebc0ee2" TYPE="swap" 
/dev/sda7: UUID="256274ac-2df6-4103-86c8-8a7ad7c70663" TYPE="swap" 
/dev/sda9: UUID="603fdd09-8ee5-4e0a-92f1-ea9a139aebe1" TYPE="ext4" 
/dev/sda10: UUID="1b209c35-eec4-4bed-a54e-feea11bd3232" TYPE="swap" 

```

sudo fdisk -l:

```
omitting empty partition (7)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x335942c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1702    13666304   27  Unknown
/dev/sda2   *        1702        1715      102400    7  HPFS/NTFS
/dev/sda3            1715       11913    81920370    7  HPFS/NTFS
/dev/sda4           11913       38914   216880129    5  Extended
/dev/sda5           37477       38914    11540480   82  Linux swap / Solaris
/dev/sda6           36998       37477     3843072   82  Linux swap / Solaris

Partition table entries are not in disk order

```

mount:


```
/dev/sda9 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)

```

Thanks forestpixie. :)

---

### Post by jjjB on 2011-07-25
In the future, you should know it's not that tough to make your own partitions. Here are some urls I read to help me figure it out on my own. Even if you're not using windows, the concepts discussed in these pages should be helpful.

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
# shows how to have data shared between the two OS's...works for me, so far

[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)
# just more talk about the concepts

I used GParted on the live CD and created the following partitions:
boot
home
windows
data (shared between the two)
swap

Swap is suggested to be on a different physical drive than your linux install. I also read somewhere that you can run swap directly from RAM, but have not tried this. It's suggested to do this if you have a lot of RAM and a small amount of hard drive space.

Cheers

---

### Post by Elfy on 2011-07-25
Well you'll need to find it :)

Boot it - start gparted from the sys/admin menu.

You can remove these - they are not used.

/dev/sda5
/dev/sda6
/dev/sda7

Bit concerned that there are missing partitions. Post a screenshot of gparted from the livecd.

Once you've deleted the old swaps you can move the unallocated space and resize the install partition to include the space - mount says the install is on sda9

---

### Post by MG&amp;TL on 2011-07-25
HELP!

After I rebooted after running those commands, it went to:

grub rescue>

So I booted from live cd, only for it to tell me that there is no OS on the system, so therefore Windows has gone. I do not have a disk, it came pre-installed.

**I'm trying not to get cross, but what did those commands actually do? And is it possible to get my Windows back? I don't want to install Ubuntu in case it wipes my data that might be recovrable, so I'm ranting from another pc.**

:confused::mad::frown:#-o

EDIT: not bothered about the data, more the OS. £100.

---

### Post by Elfy on 2011-07-25
> After I rebooted after running those commands, it went to:What commands?

```
omitting empty partition (7)
```This is what I was alluding to here > Bit concerned that there are missing partitions.  It's possible that whatever it was you did in Disk Utility has caused some issues. 

The commands I have given you wouldn't have changed anything yet.

Possibly the partition table has become corrupt making it appear as if there is no install.

---

### Post by MG&amp;TL on 2011-07-25
Possibly. I tried to 'delete a partition' -the first one along, and it did not come up with any errors like 'in use'

Can I install ubuntu somewhere, and then use grub to get back to windows? I'd have to be very careful not to wipe windows with Ubuntu. Sorry, angry. :(
Not your fault.

---

### Post by Wim Sturkenboom on 2011-07-25
> **MG&TL said:**
> Yep, I used the Ubuntu installer. I CAN use the manual one, it's just much easier not to.
If you call '*cleaning up afterwards*' easier, you're right :lolflag:

---

### Post by Elfy on 2011-07-25
> Can I install ubuntu somewhere, and then use grub to get back to windows? I'd have to be very careful not to wipe windows with Ubuntu. Sorry, angry.
Not your fault.I would not do anything at all until you're completely sure.

_Certainly I'd not write to the disk in anyway at all until I'd recovered what you had previously._

You can apparently use testdisk to recover partition tables. [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

However it's not something I've ever had cause to do and will not be of much help. 

I can though change the thread title to more accurately reflect the issue.

---

### Post by MG&amp;TL on 2011-07-25
Please do. Is it likely to be recoverable, or is it a 'just maybe' kind of thing?

---

### Post by Elfy on 2011-07-25
It's likely to be recoverable - many have managed to do so here, that's not to say it is 100%.

I will reiterate - don't do anything to it other than boot a livecd on the machine for the moment.

Another thing you can do once you have the livecd - go here and run the script - it'll get a lot of information that you can paste here.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by MG&amp;TL on 2011-07-25
Got the cd, so just 'try ubuntu'-then get the script, and post output. :D Easy enough.

---

### Post by MG&amp;TL on 2011-07-25
Script does not run-

```
ubuntu@ubuntu:~/Desktop$ sudo sh boot_info_script.sh 

boot_info_script version: 0.60        [17 May 2011]

boot_info_script.sh: 353: Syntax error: "(" unexpected (expecting "fi")

```

What do I do now?

---

### Post by Elfy on 2011-07-25
Try again - works fine here.

---

### Post by MG&amp;TL on 2011-07-25
On a live cd? I shall try...Disk Utility still recognizes the partitions, but neither the installer nor grub notices. Can I do something with Utility or another app that replaces the swap I deleted? I suppose there's no reason why I could not make some new partitions labelled swap and then reboot and deal with problems...I shall await instruction. :)

Thanks for helping an idiot....

---

### Post by MG&amp;TL on 2011-07-25
Ah...finally. 

 ```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos9)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,334,655    27,332,608  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,334,656    27,539,455       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,539,456   191,380,195   163,840,740   7 NTFS / exFAT / HPFS
/dev/sda4         191,381,502   625,141,759   433,760,258   5 Extended
/dev/sda5         602,060,800   625,141,759    23,080,960  82 Linux swap / Solaris
/dev/sda6         594,366,464   602,052,607     7,686,144  82 Linux swap / Solaris
Invalid MBR Signature found.
Empty Partition.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C8AA06B5AA069FD4                       ntfs       Recovery
/dev/sda2        8A301D04301CF8C1                       ntfs       System Reserved
/dev/sda3        38921F23921EE562                       ntfs       
/dev/sda5        c570ce31-e22f-43d6-bc99-f93b0505f38b   swap       
/dev/sda6        2c685e84-3120-496f-ab18-e5f26ebc0ee2   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  02 d2 00 00 00 00 07 00  98 86 03 2c 00 00 00 00  |...........,....|
00000010  90 83 2b 0b a0 f8 ff ff  ff ff ff ff 00 10 00 00  |..+.............|
00000020  a0 00 00 00 01 00 00 00  01 d2 00 00 00 00 05 00  |................|
00000030  2c 87 03 2c 00 00 00 00  00 ab a3 0a a0 f8 ff ff  |,..,............|
00000040  ff ff ff ff 00 10 00 00  a0 00 00 00 01 00 00 00  |................|
00000050  00 d2 00 00 00 00 06 00  de 89 03 2c 00 00 00 00  |...........,....|
00000060  50 3b 16 0b a0 f8 ff ff  ff ff ff ff 00 10 00 00  |P;..............|
00000070  a0 00 00 00 01 00 00 00  cb d3 00 00 00 00 06 00  |................|
00000080  af 8b 03 2c 00 00 00 00  f0 e6 c1 08 a0 f8 ff ff  |...,............|
00000090  ff ff ff ff 00 10 00 00  a0 00 00 00 01 00 00 00  |................|
000000a0  83 d2 00 00 00 00 08 00  08 ae 03 2c 00 00 00 00  |...........,....|
000000b0  b0 c1 7b 0c a0 f8 ff ff  ff ff ff ff 00 10 00 00  |..{.............|
000000c0  a0 00 00 00 01 00 00 00  26 d2 00 00 00 00 07 00  |........&.......|
000000d0  d5 af 03 2c 00 00 00 00  10 d4 a5 02 a0 f8 ff ff  |...,............|
000000e0  ff ff ff ff 00 10 00 00  a0 00 00 00 01 00 00 00  |................|
000000f0  d6 d2 00 00 00 00 06 00  6e b3 03 2c 00 00 00 00  |........n..,....|
00000100  60 0b dd 0d a0 f8 ff ff  ff ff ff ff 00 10 00 00  |`...............|
00000110  a0 00 00 00 01 00 00 00  d5 d2 00 00 00 00 07 00  |................|
00000120  e0 b9 03 2c 00 00 00 00  c0 fa 79 0a a0 f8 ff ff  |...,......y.....|
00000130  ff ff ff ff 00 10 00 00  a0 00 00 00 01 00 00 00  |................|
00000140  0a 45 01 00 00 00 05 00  46 c2 03 2c 00 00 00 00  |.E......F..,....|
00000150  d0 a1 9d 0c a0 f8 ff ff  ff ff ff ff 00 10 00 00  |................|
00000160  a0 00 00 00 01 00 00 00  97 8a 00 00 00 00 17 00  |................|
00000170  de d7 03 2c 00 00 00 00  50 f2 ec 08 a0 f8 ff ff  |...,....P.......|
00000180  ff ff ff ff 00 10 00 00  a0 00 00 00 01 00 00 00  |................|
00000190  e1 d1 00 00 00 00 08 00  a7 d8 03 2c 00 00 00 00  |...........,....|
000001a0  70 02 ac 0b a0 f8 ff ff  ff ff ff ff 00 10 00 00  |p...............|
000001b0  a0 00 00 00 01 00 00 00  5d d2 00 00 00 00 00 fe  |........].......|
000001c0  ff ff 82 fe ff ff 02 78  7a 18 00 30 60 01 00 fe  |.......xz..0`...|
000001d0  ff ff 05 fe ff ff 47 ea  04 18 bb 6d 75 00 00 00  |......G....mu...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by MG&amp;TL on 2011-07-25
Failing that, I have the key for Windows7 on the back of my laptop, I don't suppose there's a way to download a .iso or whatever, then enter the key afterwards? Or does that not work? I can always re-install ubuntu, whereas I'm not paying 100 pounds for insurance against idiocy.

---

### Post by MG&amp;TL on 2011-07-25
Testdisk returns this after a 'deep search':

```
TestDisk 6.12, Data Recovery Utility, May 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63

The harddisk (320 GB / 298 GiB) seems too small! (< 2049 GB / 1908 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                23679 139 13 47327  56 25  379899904
   Linux                23680 176 49 47328  93 61  379899904
   Linux                23681 149 21 47329  66 33  379899904
   Linux                23682 154 25 47330  71 37  379899904
   Linux                23683 224 30 47331 141 42  379899904
   Linux                23691 134 60 47339  52  9  379899904
   Linux                24468  70 51 49552 204 60  402982912
   Linux                24470  80 59 49554 215  5  402982912
   Linux                24475 106 16 49559 240 25  402982912
   Linux                24729 222  6 50772  75 55  418371584

[ Continue ]
EXT4 Large file Sparse superblock Recover, 194 GB / 181 GiB

```

If it helps.

---

### Post by oldfred on 2011-07-25
It looks like your windows partitions are still there (sda1 recovery, sda2 system boot, & sda3 system), cannot be 100% sure they are not part of partition table issues, but it is less likely. You may be able to reinstall a windows boot loader & make it work. But you really need to fix partition table issues before anything else or you will have bigger issues later.

First back up current partition table and store file to separate disk.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

Post the PT.txt just to see what it says. I cannot see a specific partition table issue other than the reported:
Invalid MBR Signature found.
Empty Partition.

Did you have data in the Linux partitions you need to recover, or is reinstalling from scratch a possibility?

---

### Post by MG&amp;TL on 2011-07-26
Not fussed about data or linux, can always reinstall those later. How would I back up my partition table?

Reinstalling from scratch is a definite possibility, I just need to keep windows. In fact, I'm not bothered about data on windows, just windows. I hate it, but I need it.

Thank you for all the help so far.

---

### Post by MG&amp;TL on 2011-07-26
"-d" isn't supported. did you mean:

-b, -c, -h, -u, -v, -C, -H, -S.

Thanks! And once I've done that where do I find 'PT.txt?'

---

### Post by MG&amp;TL on 2011-07-26
Could I remove all the partitions that Ubuntu has via disk Utility, and would that remove grub, assumably the Windows boot loader is still there?

---

### Post by wildmanne39 on 2011-07-26
Hi, no it will not work that way, you should wait until tomorrow for oldfred he is one of the best with these issues. I could try to walk you through it but I am to tired tonight I might make a mistake.

---

### Post by MG&amp;TL on 2011-07-26
First thing in the morning here...thanks wildmanne, I will. I have managed to get a windows recovery disk though, so I might try that and let you know how I get on.

---

### Post by wildmanne39 on 2011-07-26
Hi, your welcome!

---

### Post by MG&amp;TL on 2011-07-26
I have my laptop back! I used a winows recovery disk from the web and it worked, restoring the MBR. Thing is, I now have an 80gb windows, and 240gb of rubbish, broken Ubuntu :(, and free space. How can I expand windows to fill the drive? 

And don't worry, people, I have Ubuntu on my other machine, and I'll run virtualbox or similiar on my laptop. So you haven't lost a member.

Thanks to all who posted, especially forestpixie and oldfred. :)

---

### Post by Elfy on 2011-07-26
I'd be inclined to use the windows disk management tool - whatever it's called to do that now you've got it working and you have ubuntu elsewhere.

If windows doesn't see the partitions at all, delete them from your livecd gparted and then boot windows to do the rest of it.

Glad you're sorted at least and thanks for the thanks.

---

### Post by MG&amp;TL on 2011-07-26
> **forestpiskie said:**
> 

Glad you're sorted at least and thanks for the thanks.
No problem. :D

It's (wait for it!) "Windows disk management tool", surprisingly :)It sees the partitions fine.

Thanks again for all the help, particularly as it continued when I got angry with one or two of you...:(

---

### Post by Elfy on 2011-07-26
> **MG&TL said:**
> Thanks again for all the help, particularly as it continued when I got angry with one or two of you...:(Thanks for that - last windows os I used in anger was w2k - long time gone now so windows stuff is either a search or a dig about in the memory ;)

Been there done that - if I had been _that_ upset you'd not be posting now :D 

Added to which I knew I'd not done anything to cause the issue so it was about helping you get to the bottom of it :)

Good luck. 

Might be a good time to look into a suitable backup plan. Possibly it might also be an idea to look at cloning partitions. 

These are search engines I use for ubuntu, both of which can be added to the ff search bar. 

[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by wildmanne39 on 2011-07-26
Hi, I am glad you got it working again.

---

### Post by MG&amp;TL on 2011-07-26
Very cool. I can search google, the only stuff I could find was about recovering from your windows cd, which I don't have. :(

I know I wouldn't be posting, hence the boot-licking. :)

Thanks again, and Ill mark the thread solved.

---

