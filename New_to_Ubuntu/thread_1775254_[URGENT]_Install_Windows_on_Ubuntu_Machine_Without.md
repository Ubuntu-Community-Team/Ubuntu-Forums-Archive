---
title: "[URGENT] Install Windows on Ubuntu Machine Without Data Loss"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by AMcKee on 2011-06-04
Hello Everyone,

First off, I just want to thank you for reading this!
I'm a bit of a Linux noob (and by "a bit" I mean "a massive" ) and I need some help here.
Not only does Ubuntu not recognise my graphics card (there is apparently no workaround, I've checked), but it also doesn't work with many Steam games, or XNA based games.
I also have problems getting it to boot sometimes, as sometimes it doesn't recognise either the graphics card or built in graphics.

_**THE SITUATION:**_

Basically, I want to reinstall Windows 7 (the OS that shipped with my laptop) parallel to Ubuntu.
Although Ubuntu has it's merits, I occasionally need to go back to Windows due to:

[LIST]
[*]Software incompatibility (that can't be fixed by WINE)
[*]Unusable game library (the steam games that I have don't work with Ubuntu)
[*]Time Constraints (Ubuntu has lots of problems on my machine and is often slow due to incompatible hardware)
[*]Work requirements (I often need to program things in languages that do not function on Ubuntu)
[/LIST]
Basically, I want Windows 7 on my machine so I can use the basic functions that I am unable to perform on Ubuntu.
Unfortunately, a new laptop that is more "Ubuntu-Compatible" is out of the question, as this laptop was both expensive and next to new. 
I don't want to waste my money just because I didn't plan on Linux systems.

_**THE MAIN QUESTION:**_

I don't have the Install Disk for windows 7. However, I do have the license and serial for it.
Is it legal to torrent the .ISO of Windows 7, burn it to a disk, and install it using my (legal) serial?
Would this remove Ubuntu and all my files? If so, is there a way to prevent this?

BTW, I am using an HP-DM4. If anyone knows of a place I can download the Windows kernel with my drivers (e.g., stock HP-DM4 .ISO), please let me know. I couldn't find anything like that when I searched, but I am sure that I have seen it somewhere...

Thanks again for your time. 
As a Ubuntu/Linux noob, I really appreciate it!

Andrew McKee (AMcKee)

---

### Post by oldfred on 2011-06-04
Either spend the money for a full windows install CD/DVD or contact HP and see if they will send you a recovery DVD. 

Did you not make the recovery DVDs from your system before you installed Ubuntu. Or do you still have the recovery partition on your drive.

If you want massive virus' and who knows what else download something that may say its windows.

---

### Post by themusicalduck on 2011-06-04
If you do still want to get Ubuntu working on your laptop, it might be worth making a thread asking for help with that too.

It looks like the laptop you have has an ATI graphics card, which should work pretty well in almost all cases.

You might have tried this already, but if not, have you tried searching for Additional Drivers (in Unity) or if on 10.10, then look for Additional Drivers under System > Administration?

You might be able to install the ATI graphics drivers through that.

Having said that, I would't expect much joy from trying to get Steam or other games to work especially well.

---

### Post by wep940 on 2011-06-04
+1   NEVER download an "bootleg" OS (and I refrain from other things as well) via a torrent as it will normally be full of all kinds a nasty things you don't want.
 
+1  Did you make recovery CDs or DVDs?  I know on my HP desktop I bought about 4 years ago you had to make recovery disks and you could only do it once.  They worked in conjuction with the recovery partition to restore things back to "as delivered from the factory" condition.
 
Lacking those disks, and lacking an OS disk, you will need to buy a copy of Windows 7 again.  Check some of the computer places - sometimes places like MicroCenter have them for under $100.  Of course, you'll still need to download and install all of the drivers from HP for the PC as well.
 
You have in the post title "Without Data Loss" - are you refering to data you have in your Ubuntu installation the you will need in your Windows installation?

---

### Post by MoebusNet on 2011-06-04
if you have data on your machine that you want to/need to save, before you do anything else, please allow me to recommend you look into backing up your data. You can back up to Ubuntu One, to an external USB drive, to DVD's or CD's or to flash disk drives. I promise you that the time you spend to backup your data will save you a lot of grief as you work to straighten out your machine.

The community documentation at:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

can be a big help. I personally use grsync to back up to an external USB drive, but read up on the subject and make a choice.

There are only two kinds of people: those who backup their data, and those who wish they had.

---

### Post by HermanAB on 2011-06-04
Hmm, well, dual boot is so 20th century...

Install VMware Player or Virtualbox and make a Windows virtual machine.  The run Windows in a window, where it belongs.

Also, VMware has a migration tool that can be used to turn a running Windows installation into a VM.

---

### Post by wep940 on 2011-06-04
+1  You have plenty of hardware to support a virtual machine.  Your existing data would remain in Ubuntu, and running a VM Windows crashes/lock-ups, etc., only result in needing to reboot the VM from within Ubuntu - no need to reboot your entire PC.

However, I suspect your biggest concern at the moment is actually getting a valid copy of Windows so you can load it either for dual-boot or in a VM - either way you need the OS.

---

### Post by ILoveYorkies on 2011-06-05
Hi, 
Or you could try to install to an external hard  drive ( or a flash drive  like I have done ) after backing up your Ubuntu data and programs that you want to keep. You should backup anyway. Then install, Win 7, if it doesn't offer to dual boot, you could overwrite your Ubuntu and you could either install just Grub2 bootloader to  the flash or get a 8 or 16 gb thumbdrive and partition it  with Gparted  from a  livecd or liveusb. First  while in Windows change the thumbdrive from  removable (to write cache so you have to always use shutdown safely  like  when using an external hard drive). Then use a livecd choose try Ubuntu  not install. If it boots okay then go to apps and pick Gparted and  partition the drive giving 300mbs or less to Grub then you need a root  (/) partition then  a a swapfile and a /home partition. Then use disk  utility to double check which is the the dev names so you install to the  correct drive so you don't overwrite your Win partitions nor it's mbr.  Or you could install grub to a 4gb or less thumbdrive after partitioning  your main Win partition most likely c drive, shrinking it so you can  make another partition for Linux. If you do that, MAKE SURE YOU BACKUP  OR COPY ALL THE DATA YOU NEED TO KEEP! Shrinking your partition with  software for Win or using Gparted usually doesn't BUT IT CAN CORRUPT OR  ERASE DATA!  If you IMPROPERLY INSTALL GRUB YOU COULD MESS UP Windows  MBR BOOTLOADER! That's why I use flash drives and use the "other" check  box during install instead of allowing Ubuntu to choose everything ( using Ubuntu 11.04 ). I  can then choose  the devices to partition myself.  I just use the key to pause post so I  can choose which drive to boot from, In my case I press Esc then F9 and  it lists my Grub drive named Sandisk. I have to do that every time  I  want to boot Natty but that's just the way I wanted it. If don't then  just go into your bios uttility and move the Ubuntu drive to 1st place  then Windows drive to 2nd place then every you power on or reboot it looks for your Grub drive  to boot from. If it doesn't find it, it boots directly into Win again. So  far this method has worked for  me. Please make backups regularly. I think you should get recovery disks from HP. I hope my suggestion about what works for me isn't out of line for you, just a newbie trying to help.

---

### Post by AMcKee on 2011-06-18
Thanks everyone for your replies.

Unfortunately, I didn't make backup disks before I installed ubuntu, as I thought I already had some.
^^First problem
Secondly, the drivers don't work. I have Radeon 5000 series on my laptop, and what comes up in the additional drivers is "ATI/AMD Proprietary FGLRX graphics driver" However, whenever I install that, I either get A) a black screen B) an error message from ATI catalyst saying it can't find the driver / hardware. I haven't found any documentation that works/solves this problem
^^Second problem, not checking ubuntu documentation about proprietary drivers
Thirdly, I can't us VMWare or similar products, as although I can get it to boot, I can't play any decent games with even 1 FPS as I am forced to use the crappy "Discrete" graphics built in to the motherboard, not the graphics card that doesn't work.

Any ideas no that I have elaborated?

Thanks,

Andrew

---

