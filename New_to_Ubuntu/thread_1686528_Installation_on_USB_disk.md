---
title: "Installation on USB disk"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by wasps on 2011-02-12
Hi,

I've been playing with Ubuntu 10.10.
So far I've been running a Live disk install on a USB disk.

Is that the only way to run on a USB disk?

Is it possible to do a full installation onto a USB disk, or should I always be running it as a Live disk?

if that is the case, is there any way to get it to automatically start as a Live disk, rather than prompting me to install it on the computer?


Thank you
Steve

---

### Post by uRock on 2011-02-12
If you want to install to the USB drive, then it may be best to disconnect your internal HDD, so that the boot loaders do not get mixed up. You can install Ubuntu to the USB as if it were an HDD.

---

### Post by oldfred on 2011-02-12
As uRock says the safest way is to disconnect internal drive. But you can manually partition in advance and then you have a combo box on which drive to install the grub loader into. Otherwise grub likes to install to sda or usually your internal drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by FatBear on 2011-02-12
I just attempted this very thing and it didn't work.  (That's why I searched around and found this thread.)  I physically disconnected the hard drives in my system so the only drives were the CD and the USB memory stick (Sandisk Cruzer Extreme 16GB.)  I installed to the USB stick and the installation seemed to go fine.  At the end it said installation was successful and that I should restart the system.  I did so, but it won't boot.  The computer (Dell Precision 390) reports the two drives are missing (they are) then says press F1 to continue or F2 for setup.  If I press F1, nothing happens.  If I press F2 I can check the boot sequence.  It is setup to boot from CD first, then hard drive, then USB.  I changed it so USB was above hard drive, but it still won't boot.  

I want to be able to plug this memory stick into other systems and boot on it.  Any ideas?

Thanks,

--FatBear

---

### Post by uRock on 2011-02-12
> **FatBear said:**
> I just attempted this very thing and it didn't work.  (That's why I searched around and found this thread.)  I physically disconnected the hard drives in my system so the only drives were the CD and the USB memory stick (Sandisk Cruzer Extreme 16GB.)  I installed to the USB stick and the installation seemed to go fine.  At the end it said installation was successful and that I should restart the system.  I did so, but it won't boot.  The computer (Dell Precision 390) reports the two drives are missing (they are) then says press F1 to continue or F2 for setup.  If I press F1, nothing happens.  If I press F2 I can check the boot sequence.  It is setup to boot from CD first, then hard drive, then USB.  I changed it so USB was above hard drive, but it still won't boot.  

I want to be able to plug this memory stick into other systems and boot on it.  Any ideas?

Thanks,

--FatBear
Did you remove the U3 software first? If not, then it will give you problems until you do.

---

### Post by Hedgehog1 on 2011-02-12
I am posting this using a USB stick installation I did (late) last night.

I cheated and used VirtualBox and created a virtual machine that had no hard drive.  I used the ISO of Ubuntu 10.10 desktop as the CD and the 16gig USB stick.  This mimics the act of 'unhooking the hard drive'.  In all honestly, disconnecting the hard drive would have been easier - but I was looking for the **maximum-nerdy-solution** :KS .

Today (after booting up normally to check email and do some real work) I inserted the USB stick and rebooted the computer.  For my MSI motherboard, I had to press F11 to get a boot list, and then selected the USB stick.

Because I want this to boot on any PC, I removed the proprietary drivers package.  I also removed a number of software packages I will not need on this portable version to save space. 

Right now the Update Manager is installing 253 packages.

I will say the USB stick is an older one, and not very fast.  Once it is booted up the performance is workable.

So... I have an Ubuntu workstation for fits in my pocket.

How cool is that?!?!?! 

p.s. Just checked Update Manager - it is about 1/2 way through applying the changes.

---

### Post by C.S.Cameron on 2011-02-12
Following step by step for Full install of 10.10 to USB device, partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by tednix on 2011-02-12
Here is a longer explanation very similar to C.S. Cameron's post.

[http://ubuntuforums.org/showthread.php?t=1650699&highlight=avoid+wubi](http://ubuntuforums.org/showthread.php?t=1650699&highlight=avoid+wubi)

There are some slight differences because the linked post contains instructions for the 10.04 installer and things have changed in 10.10.

Initially I installed to a 8 gig USB stick but found that performance was quite slow so I reformatted an old 60 gig external USB hard drive and things are now much better.

---

### Post by Hedgehog1 on 2011-02-12
> **tednix said:**
> Here is a longer explanation very similar to C.S. Cameron's post.

[http://ubuntuforums.org/showthread.php?t=1650699&highlight=avoid+wubi](http://ubuntuforums.org/showthread.php?t=1650699&highlight=avoid+wubi)

There are some slight differences because the linked post contains instructions for the 10.04 installer and things have changed in 10.10.

Initially I installed to a 8 gig USB stick but found that performance was quite slow so I reformatted an old 60 gig external USB hard drive and things are now much better.

I completely agree about using an external USB hard drive over a USB stick for better performance.  Mine works (I am still posting from it) but this first round of updates after installing from the CD is still running over an hour later.

This same update on a VirtualBox test install yesterday took 90 seconds. Same CPU & Memory, but much slower 'drive' speed.

Unless you need ultimate portability, an external USB HARD drive is a cheap and cheerful solution.

It also give you room for Music and Movies...

---

### Post by tednix on 2011-02-12
I experimented with VirtualBox running Windows XP from Ubuntu 10.10 on my external HD and found it to be too slow.  My 2 yr old Toshiba laptop has an eSATA port and I may upgrade to an external eSATA HD to improve drive speed.
Initially I was worried because of all of the GRUB errors that I read about here in the forums  But as I gain experience the simple thing to do is just go ahead with a dual boot and by pass the hassles and expense of another external drive.

---

### Post by C.S.Cameron on 2011-02-12
I have Autocad running in XP on a virtual machine in Ubuntu on thumbdrive.
Now that is slow.

---

### Post by Hedgehog1 on 2011-02-12
> **C.S.Cameron said:**
> I have Autocad running in XP on a virtual machine in Ubuntu on thumbdrive.
Now that is slow.

I yield to you the award I just invented:

I hereby present you with: *'The slowest possible way to run Autocad and still use a computer to do it'* Award.

:lolflag:

I feel a little better about the USB install of Ubuntu I am still using to post with *because all the 253 updates have still not finished updating*.  Chromium works OK, at least (at this post proves).

:KS

---

