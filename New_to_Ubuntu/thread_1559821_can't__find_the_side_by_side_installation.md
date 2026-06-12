---
title: "can't  find the side by side installation"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by adam3531 on 2010-08-24
hi everybody,
I downloaded form the site the latest ubuntu 10,04 and I'm trying to install it on my 
netbook(asus 1201N), I did exactly as the Instructions said to make a usb stick,
but in the installation I can't see the option of installing side by side and I want to keep my
windows 7.
what should I do?

---

### Post by LiquidMeson on 2010-08-24
I'm assuming that the usb stick worked, you clicked on try ubuntu, and when through install till you got to this part?

[http://www.hackourlives.com/wp-content/uploads/2010/05/Ubuntu-9.10-Install_012.png](http://www.hackourlives.com/wp-content/uploads/2010/05/Ubuntu-9.10-Install_012.png)

More Pictures.
[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/)
ignore pictures/steps 4-10 and just pick "install side by side"

If your not seeing the first picture then something when wrong with the usb stick or pc.

Need more info :o

---

### Post by wilee-nilee on 2010-08-24
> **adam3531 said:**
> hi everybody,
I downloaded form the site the latest ubuntu 10,04 and I'm trying to install it on my 
netbook(asus 1201N), I did exactly as the Instructions said to make a usb stick,
but in the installation I can't see the option of installing side by side and I want to keep my
windows 7.
what should I do?

Boot the live cd and post the output of this command in the terminal
```
sudo fdsik -l
```

Your problem may be that you have 4 primary partitions already.

---

### Post by adam3531 on 2010-08-24
here what I got using sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x593e9087

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104857600    7  HPFS/NTFS
/dev/sda2           13055       37606   197208064    7  HPFS/NTFS
/dev/sda3           37606       38911    10485760   1b  Hidden W95 FAT32
/dev/sda4           38911       38913       16224+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 4041 MB, 4041211392 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32

what should I do?

---

### Post by wilee-nilee on 2010-08-24
I thought so you have 4 primaries already. Post the boot script in my sig so we can see what all the partitions are. Post the script output in code tags as described in the sig.

What you probably have is a firmware partition and a recovery partition and 2 partitions one C one D

---

### Post by adam3531 on 2010-08-24
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,717,248   604,133,375   394,416,128   7 HPFS/NTFS
/dev/sda3         604,133,376   625,104,895    20,971,520  1b Hidden W95 FAT32
/dev/sda4         625,104,896   625,137,344        32,449  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4041 MB, 4041211392 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892991 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        327429DC7429A397                       ntfs                                     
/dev/sda2        82902D86902D81B1                       ntfs                                     
/dev/sda3        E42B-441A                              vfat       &#136;&#136;&#136;&#136;&#136;&#136;&#136;&#136;&#136;&#136;&#136;                   
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B817-B7ED                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

what is the next step?

---

### Post by wilee-nilee on 2010-08-24
The people who are really good at this generally are on during the day US time. I am to tired to read the script correctly and don't want to do any damage here. Bump your thread if you can during the day. I will look again tomorrow after some sleep.

---

### Post by adam3531 on 2010-08-24
bumpp

---

### Post by adam3531 on 2010-08-24
bumpin' again sorry :/

---

### Post by ranch hand on 2010-08-24
You may not know this but there are people that think I am crazy because I think you should install Linux on a / (root) and a /home partition.

4 fing partitions for one OS?  Give me a break.  This is just MS trying to insure that no one installs any other OS.  What a crock.

All HDDs currently follow the DOS partitioning rules that limit you to 4 primary partitions.  All of yours are primary partitions.

You actually need 2 for Linux, at least 1 for the OS and 1 for swap.

There is such thing as an "extended" partition that is a type of Primary but allows you to create any number of "logical" partitions within it.

So what you need to do, normally, is resize your MS partitions to make room and then make an extended partition and install Linux in it with however many partitions you want.

As I will not have any MS in the house I am too ignorant to suggest a cure here.  I have a sneaking suspicion that sda2 is not needed and could be deleted.  DO NOT do that unless some one who actually will run that MS crap tells you it is safe to do.

If you can do that, then sda3 could be made smaller and moved to the left.

I believe that then moving sda4 to the left would also be safe.

At that time you could then create an extended partition at the right hand end of your drive for Linux.

Hopefully some one will jump in here and tell you that you can do something like that.

One thing that may help them is if you would answer this question;

Is the W7 install a fresh install or an upgrade from Vista?

---

### Post by adam3531 on 2010-08-24
I bought the computer with windows 7 so I believe that is a fresh install

---

### Post by cariboo on 2010-08-24
Please don't bump your thread until at leats 24 hours has elapsed, we are all volunteers here, and it may take a while for the person that can answer your question, to see it.

---

### Post by pania on 2010-08-24
Incorrect information.

---

### Post by LiquidMeson on 2010-08-24
Not sure how things have progressed from here. But if your feeling risky, (back up the important stuff), I would run the live usb, system>admin>disk utility. And delete all partitions except the large one. Once thats done restart and see if windows works. If so, it should be smooth sailing from there.

Most likely the other partitions are not necessary. Assuming you still have the windows key (on the bottom of the laptop) and a Windows install disk you should be able to recover if anything hazards should arise.

---

### Post by ranch hand on 2010-08-24
Now see, you should listen to these fellers.

If it was me it would be easy.  Format the whole drive so that there is one Primary partition ext4 of 25 Gb and one extended partition with a swap at the end and an ext4 partition of about 75 Gb and the beginning, the rest unused for future use.  No MS.  No mess.

Seeing how you actually want MS on there, these guys have been there and have a good idea what will work to accomplish this end result.

MS and the OEMs are not real good at playing nice with other OS'.  They are, rightly, afraid you may not continue to buy their stuff is you try something else.

---

### Post by Reiger on 2010-08-24
Do you have any external harddisk or USB flash drive capable of storing ~25GB of data? That would be helpful for fixing this problem.

The idea is as follows:

(a) You are using 4 primary partitions already, which is suboptimal. It would be better to convert this scheme to: 2 primary partitions (Windows C driver and firmware/recovery partition) plus a 3rd so-called extended partition. The 3rd partition should be as large as possible because this will be split in 4 logical partitions: one to contain your D drive, one to contain your Ubuntu root (/) file system, one to contain swap and one to contain your Ubuntu /home filesystem (your home directory basically, the difference between / and /home will be analogous to the difference between C & D drives in the old setup). The swap partition should be roughly the same size as the amount of RAM you have (it is not strictly necessary, but if you make it too small you will be unable to hibernate and if you make it too large you will be wasting your precious disk space).

If you want you can use Windows control panel to create “recovery” disks (at least you could in Vista, haven't tried with 7 yet). If you have successfully created such recovery disks it should be safe to dump the recovery partition on the hard disk because now you will have a copy on DVD's, too. With only 25GB to spend that might be tempting.

(b) To do (a) it is best to backup your data first. Also it is a good idea to assign “labels”/“names” to the Windows drives (which identify these partitions by another means than their drive letter) as these labels can be used to identify the drives under Linux, too.

(c) To make the actual partitions you should use the manual partitioning option in the Ubuntu installer, don't bother with the Windows partitioner as it does not work nearly as well as tools Ubuntu uses. The tool allows you to delete and shrink partitions.

I am not sure how much space Windows 7 requires, but I would allocate at a minimum 10GB of data to the / + swap + /boot filesystems. I have a 80GB SSD of which I allocated 20 to /, 53 to /home, 4 to swap, and 3 to /opt. (/opt being the place where I dump scripts and programs that do not come from the Ubuntu package repositories.) I currently use ~36% of the / partition (7.2GB). I run a fairly fat desktop and not all of that data is strictly necessary or even used, though; so with a bit of good sense ~8GB should be a decent fit.

---

### Post by adam3531 on 2010-08-25
what a mess,
I thought its a small problem :(

I dont have time for this now and I dont know even how to do all the things you suggested.

I think I will give up on linux in the near future.

thank you all for the help.

---

### Post by Mark Phelps on 2010-08-25
Actually ... it generally is a SMALL problem to do what you want ... but in your case, it is NOT because of two reasons:


1) ASUS (not MS) decided to saddle you with a 4-primary-partition formatting scheme.  While I suspect this was done intentionally to discourage installing other OS's, it could also simply be stupidity on their part.  This make repartitioning an absolute necessity.

2) All these folks telling you to simply wipe and reinstall are ignoring two problems in your case.  First, since the machine came preloaded with Win7, you have NO installation medium that you can do to reload the OS.  All you have (at best) is a Recover CD that (most probably) contains a version of WinPE that will boot into an environment an then look for a Win7 image file stored in a partition on your drive. No file; no restore.

Second, I believe that your Netbook does NOT have an optical drive.  IF it also does not have the ability to boot from an external optical drive (or if you don't have one), even having Win7 installation media (which comes on a DVD) will not help you.

The risk you run messing around with the solutions folks have proposed is that you wipe out Win7 -- with no way at all of getting it back.

I certainly understand someone choosing NOT to take that risk.

---

### Post by Reiger on 2010-08-25
Mark Phelps: all of us are assuming that the OP has an external DVD R/W station (connected via USB). If that is not the case installing Ubuntu is not going to work very well because Ubuntu doesn't distribute USB images and to convert an Ubuntu CD image into an USB one you'd need a working Ubuntu installation elsewhere.

Also I wouldn't worry too much about not having installation mediums. First of all, the last two times I bought a something (a laptop to be precise) which came preloaded with a copy of Windows the manufacturer was kind enough to include the installation medium in the box as well. If you were wondering those manufactures were Asus and Dell respectively. Secondly repartitioning need not touch the C:\ drive at all, so there is no need to wipe the W7 installation or render it otherwise rendered unusable.

---

### Post by LiquidMeson on 2010-08-25
Yo Dawg I herd you like partitions.

Anyway, Ubuntu is pretty easy to use. But sometimes yah just gotta get rid of all the old junk first. If you ever back up your important files, just format the whole thing upon install. Much much easier. But no going back.

---

### Post by bennachie on 2010-08-25
This is almost certainly a very simple problem. Every ASUS netbook I have used has the same initial partitioning scheme. From a Windows perspective, you have a C: partition formatted as NTFS in which W7 is installed, a D: partition, also formatted as NTFS, and initially unused (but, obviously, accessible to the user for data), a recovery partition (which can be used to repair the W7 installation or to restore the system to its original factory state) and a very small "boot acceleration" partition which is largely a waste of space.

From a dual-boot perspective, this is actually quite a good scheme.

My normal approach is first to check that the D: partition (sda2) is currently empty. This is almost certainly the case unless you have explicitly chosen to store data generated by W7 there. If there is data there, move it back to the C: partition. Then, from the Ubuntu liveCD, initiate the installation. When you get to the partitioning stage, choose the "custom partitioning" option. Delete the existing sda2 partition, and create three new partitions in the free space thus created (one of, say 15GB for the "/" partition, which holds the Ubuntu system files, one for the "/home" partition - taking most of the remaining space - and one of, say, 3GB for the swap partition). Obviously, you don't try to force any of these to be primary partitions - they will thus be created as extended partitions, probably designated as sda5, sda6 and sda7.

That should work very nicely. The only small thing to watch is that the bootloader (Grub2) will offer you two Windows boot options (sda1, W7 and - usually, but YMMV - sda3, Vista). The latter is obviously your recovery partition, and you should avoid launching that unless you really do want to set everything back to its original state. If you do launch it by accident, cancel the process as soon as possible, and no harm will be done.

After a month or two of dual-booting, you will probably want to consider following the pathway suggested by ranch hand.

---

### Post by VinDSL on 2010-08-25
Heh!  Looks like the OP already gave up.  

I'll just post a screenie of my partition setup (a pic being worth 1000 words).  It might help someone...

I'm running Mint 7 & XP Home on my Asus EeePC netbook.  Works great!

As you can see, I'm running /home and swap in separate partitions, as *ranch hand* recommends.  On a permanent installation, I always do this.  If I'm just testing a distro, I don't bother with it.

BTW, you'll see an "unknown" partition (sda3).  This is some sort of weirdness that Asus uses to fastboot XP.  I suggest leaving it alone.  No telling what kind of alchemy they used there...  ;)

---

### Post by VinDSL on 2010-08-25
In case anybody notices...  XP is hidden in the screenie (above).

I got into the habit of hiding OSs from each other, in multi-booted installs.

No reason to beat that horse, in this thread, but here's my /boot/grub/menu.lst file:

```
default 0
timeout 10
color cyan/blue white/blue
gfxmenu=/boot/gfxmenu/linuxmint.message

title		Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root		(hd0,4)
hide		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,4)
hide		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Linux Mint 7 Gloria, memtest86+
root		(hd0,4)
hide		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
unhide		(hd0,0)
makeactive
chainloader	+1

```

If you're the curious type, that should give you an idea of what I'm up to...  :)

---

### Post by adam3531 on 2010-09-01
Ok I'm back,
now I have time for this. I have deleted the win 7 backup that was store in partition d:\
I have resized d:\ to be 100GB,
now I have 87GB free to install linux,
but I can't install it on this part, what should I do?

---

### Post by Elfy on 2010-09-01
You already have 4 partitions - the maximum.

Maybe find out what is on the 16Mb sda4 partition and move it to an existing partition then delete the partition. You'll be able to install then.

---

### Post by adam3531 on 2010-09-01
ok i merge the partitions,
I have 4 now
sda2 is now 187GB
how can I install using this sda only?

---

### Post by Elfy on 2010-09-01
You don't want 4 - you want 3 

If you now try and install it will want to resize one of them to make new partitions - then you'll have more than 4 again.

Which is why I said > Maybe find out what is on the 16Mb sda4 partition and move it to an existing partition then delete the partition

You will be able to install ubuntu into an extended partition with logicals inside that. 

But you can only have 4 primary partitions - an extended counts as a primary.

If you can't move data around to free a partition maybe look into wubi for the time being.

---

### Post by adam3531 on 2010-09-01
I belive the 16 MB is a boot booster. is it any good?
should I delete it?

---

### Post by Elfy on 2010-09-01
I have absolutely no idea at all what a boot booster is - I assume it's some windows thing.

I would go back to post#18 and just have another read of that. 

Make sure of what you want to do here.

The alternative at the moment is to use wubi - I'd not normally recommend it (only used it once to have a look) but it will at least allow you to install ubuntu without touching exisitng partitions.

---

