---
title: "[SOLVED] Trial By Linux"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by oilchangeguy on 2008-12-13
First my computers specs:
System Info 
Model : Asus A7N266-C
Chassis Type : Tower
Operating System : Microsoft Windows XP Professional Service Pack 3 (Build 2600) 
 
Processor 
Number Of Processors : 1
Type : AMD Athlon XP 2100+
Processors Bus Speed : 266 MHz
 
Motherboard 
Manufacturer : ASUSTeK Computer INC. 
Model : A7N266-C Rev. REV 1.xx
CPU Slot/Socket Type : Socket A (462)
Chipset Vendor : NVIDIA nForce Rev. B2
Bios Manufacturer : Award Software, Inc.
Bios Version : ASUS A7N266-C ACPI BIOS Rev 1001.E
 
Graphics 
Model : nVidia AGP NVIDIA GeForce 6200 
AGP Speed : Not Available 
Monitor : Plug and Play Monitor
 
Storage 
Hard Drive 1 : Maxtor 6L200P0 
Size : 194.48 GB
Hard Drive 2 : Maxtor 6Y200P0 
Size : 194.48 GB
Hard Drive 3 : Maxtor 6 Y080P0 
Size : 78.17 GB
 
Memory 
Total RAM Installed : 1536 MB
Type : DDR DIMM 
Used RAM Slots: 3 of 3
 
Accessories 
USB Version : Not Available 

Second, every cd used to attempt to install linux on this computer works (just not on this computer). I've tried to install linux on this computer several times over the last year. but to no avail. I don't think it can be done. Tried Mandriva Spring 2008, can't get the desktop to load. Tried Mandriva 2009 One, can't get the desktop to load. Tried Ubuntu 7.04, 7.10 no go. Tried Ubuntu 8.04 got to the desktop, and installed it. Upon reboot some cryptic error message. Tried Kubuntu 8.10 (kde looks better than gnome) got the desktop to load, got on the internet, sound worked, great let's install it. From the specs you'll note this computer has three hard drives. I disconnected all but one for this install attempt. I've had to reload Windows more than once because this computer refuses to run linux, thus creating a botched dual boot attempt. So with the one hard drive I start the install process, all goes well. Until reboot, the computer displays the dreaded grub error 18. I've tried to install several times, using several different partitioning options. And hard drive formats. The hard drive has been totaly blank, with no partitions. Or formated ntfs. The same result, grub error 18. I've tried changing this bios settings for the drive from auto, to manual, and under manual set the drive to normal. I got a screen of never ending grub. Back to auto grub error 18. So now I'm back to where I started. All hard drives plugged in. The two that are for storage are formmated ntfs, and all is well. This computer runs Windows XP Pro fine. But with Microsoft's support ending for XP in 2009 I'd like to have the option to run a linux operating system. Just a thought, do not buy or build a custom computer. There's the chance of hardware conflicts. I'm not sure what is causing my linux problems with this computer. I've run linux on other computers by itself, and as a dual boot, with no problems. But they were all store bought computers, not custom built rigs, as this one is. For the average computer user a store bought computer is fine, and cheaper than a custom rig. The 700 watt power supply for this computer cost $150.00. I could go out and buy a new computer today for less than 500.00 that has more ram, probably not more hard drive space. But I don't think I'd have the same problems trying to install linux, as I'm having with this custom computer. Anybody have any thoughts on why this computer refuses to run linux? Thanks!

---

### Post by philinux on 2008-12-13
I assume you've looked up grub 18 error. Have you tried the solution.

[http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)
Errors and solutions
Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

**This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.**

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.

---

### Post by overdrank on 2008-12-13
I am not sure you have tried this but I would remove some on the memory and try with just one slot.
How are the hard disk connected?
You may have already tried these :)

---

### Post by oilchangeguy on 2008-12-13
> **philinux said:**
> I assume you've looked up grub 18 error. Have you tried the solution.

[http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)
Errors and solutions
Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

**This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.**

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.

Hi, Phil. Yes I looked up error 18. I did not try the manual partitoning option. This computer was built somewhere around 2001 or 2002. I bought it used, and added two hard drives, replaced the video card, both optical drives, the power supply, and maxed out the ram. My main point is this. It should not be this hard to install linux on this computer. If linux ever intends to appeal to the masses, it's got to do better than this. I'm sure I'm not the only one with problems such as this.

---

### Post by oilchangeguy on 2008-12-13
> **overdrank said:**
> I am not sure you have tried this but I would remove some on the memory and try with just one slot.
How are the hard disk connected?
You may have already tried these :)

Hard drives are connected ide. Two as master and slave. And one master to an ide controller card.

---

### Post by philinux on 2008-12-13
I would try the boot partition option. The manual partitioning is not hard at all.

---

### Post by overdrank on 2008-12-13
> **oilchangeguy said:**
> Hard drives are connected ide. Two as master and slave. And one master to an ide controller card.

Ok if the card can handle all the drives you may try that. I had some issues with one motherboard with one ide channel and it would not install with the hard drive on the channel with the cd. Thats all I have :)

---

### Post by oilchangeguy on 2008-12-13
> **overdrank said:**
> Ok if the card can handle all the drives you may try that. I had some issues with one motherboard with one ide channel and it would not install with the hard drive on the channel with the cd. Thats all I have :)

The two mobo hard drives are not on the same channel as the two optical drives.

---

### Post by oilchangeguy on 2008-12-13
> **philinux said:**
> I would try the boot partition option. The manual partitioning is not hard at all.

I'll try that, at some point. when I'm in the mood to play with this computer again. But, this should not be. On the vast majority of computers you drop in the cd, follow the prompts. And 30 minutes later you've got a running linux operating system.

---

### Post by CatKiller on 2008-12-13
It could be because of the way that your drives are connected. You've installed Ubuntu, and the installer puts GRUB in the MBR of the only hard drive it can find. Then you shuffle all the hard drives around and put new drives in, which means that, in principle, the (hd0) that GRUB is looking at is no longer the same (hd0) that actually has Stage 2 of GRUB on.

It is possible, from the GRUB prompt, to find the partition that has GRUB's Stage 2, and then update GRUB to look there instead. I've not had to fiddle at the GRUB prompt, but it's something like ```
find /boot/grub/stage2
``` followed by changing the *root* option. I think. A search for "restore GRUB" will probably give you a tutorial on how to point GRUB at the right place to continue the booting process.

---

### Post by oilchangeguy on 2008-12-13
> **CatKiller said:**
> It could be because of the way that your drives are connected. You've installed Ubuntu, and the installer puts GRUB in the MBR of the only hard drive it can find. Then you shuffle all the hard drives around and put new drives in, which means that, in principle, the (hd0) that GRUB is looking at is no longer the same (hd0) that actually has Stage 2 of GRUB on.

It is possible, from the GRUB prompt, to find the partition that has GRUB's Stage 2, and then update GRUB to look there instead. I've not had to fiddle at the GRUB prompt, but it's something like ```
find /boot/grub/stage2
``` followed by changing the *root* option. I think. A search for "restore GRUB" will probably give you a tutorial on how to point GRUB at the right place to continue the booting process.

if you'll read post #1 again, you'll note that i used only one drive for the linux install. the other two were disconnected.

---

### Post by CatKiller on 2008-12-13
> **oilchangeguy said:**
> if you'll read post #1 again, you'll note that i used only one drive for the linux install. the other two were disconnected.

I'd got that part, but then (incorrectly, I guess) assumed that you'd re-connected the others before you had the boot problems since you later said they were all connected.

Is this drive connected to the motherboard's IDE controller, or your IDE controller card? Perhaps trying it in the other would be a sensible troubleshooting step.

---

### Post by oilchangeguy on 2008-12-13
> **CatKiller said:**
> I'd got that part, but then (incorrectly, I guess) assumed that you'd re-connected the others before you had the boot problems since you later said they were all connected.

Is this drive connected to the motherboard's IDE controller, or your IDE controller card? Perhaps trying it in the other would be a sensible troubleshooting step.

mobo, tried the card, and the install freezes at 5%.

---

### Post by CatKiller on 2008-12-13
> **oilchangeguy said:**
> mobo, tried the card, and the install freezes at 5%.

Have you tested the hard drive for errors? Maxtor have a utility on their website that will do it. All hard drives can have problems, but Maxtor did have a particularly bad crop for a while. I don't know if your drives would be in that timeframe.

Using memtest from the Ubuntu cd would also be a sensible precautionary test, as would cleaning the lens of your optical drive or trying a different one.

The fact that the install freezes is not an especially promising sign.

---

### Post by oilchangeguy on 2008-12-13
> **CatKiller said:**
> Have you tested the hard drive for errors? Maxtor have a utility on their website that will do it. All hard drives can have problems, but Maxtor did have a particularly bad crop for a while. I don't know if your drives would be in that timeframe.

Using memtest from the Ubuntu cd would also be a sensible precautionary test, as would cleaning the lens of your optical drive or trying a different one.

The fact that the install freezes is not an especially promising sign.

the computer is fine, except for the fact that it will not run a linux operating system. as for the ide controller card and freezing, not sure if this has anything to do with it. but i don't know how old the card is, and don't have the bios installed for it. doubt even if the install actually worked that the computer would boot from a hard drive connected to the card, and not the mobo.

---

### Post by CatKiller on 2008-12-13
> **oilchangeguy said:**
> the computer is fine

How do you know, without testing?

---

### Post by JKBurton on 2008-12-13
> **oilchangeguy said:**
> the computer is fine, except for the fact that it will not run a linux operating system.

The computer is fine except that you looked up the solution to your problem, and tossed the answer aside saying "it shouldn't be like this". Having to jump through a few hoops should be expected when working with a custom system.

I'm not trying to be snotty, just explaining what I see as one of the facts of life. I've owned maybe ten custom-built computers over the decades (starting in 1977!), and another twenty or so vendor-built ones. Most of the custom ones gave me some grief when trying to get the OS working. As you pointed out, custom-built systems are more likely to have internal conflicts. We just have to bash our way through them, one at a time.

I've even run into your exact situation where the partition was too big to boot with Microsoft a couple of times (don't remember which versions, it's been a while).

And yes, I got frustrated too! :)

---

### Post by oilchangeguy on 2008-12-13
> **CatKiller said:**
> How do you know, without testing?

the memory is ok, and the hard drives are error free. everything's been checked.

---

### Post by oilchangeguy on 2008-12-13
> **JKBurton said:**
> The computer is fine except that you looked up the solution to your problem, and tossed the answer aside saying "it shouldn't be like this". Having to jump through a few hoops should be expected when working with a custom system.

I'm not trying to be snotty, just explaining what I see as one of the facts of life. I've owned maybe ten custom-built computers over the decades (starting in 1977!), and another twenty or so vendor-built ones. Most of the custom ones gave me some grief when trying to get the OS working. As you pointed out, custom-built systems are more likely to have internal conflicts. We just have to bash our way through them, one at a time.

I've even run into your exact situation where the partition was too big to boot with Microsoft a couple of times (don't remember which versions, it's been a while).

And yes, I got frustrated too! :)

i did not toss the answer aside. i've tried various options, except for manual partitioning. and like i said, i may try this at some point. and i agree that there may be some kinks to workout. but these should arise after the os is installed. getting the os to install should be cut and dried. like i said if linux is ever going to appeal to the masses jumping through hoops to simply install the os should not be. what about the fact that most computer users barely know how to turn them on, let alone jump through hoops to install an operating system.

---

### Post by JKBurton on 2008-12-14
I agree in theory, oilchangeguy. In practice, though, the install is one of the hardest parts. It's very common for PC hardware to tell outright lies to the installer when asked things like "Do you support xyz optional feature?" and such. That sounds crazy but it's the truth.  

You don't see it in Windows much because every hardware company tests their cards with the Windows installer. When a problem appears, they either patch the card or, often, update the Windows driver to handle the incompatibility.

When they patch the card, it no longer works the way its published specs say, and that's how they end up "lying" to the installer.

If they instead update the Windows driver for their hardware, they only rarely tell the Linux folks about it. So we only find out when things start breaking.

This particular problem may only be solved when the vendors offer more pre-installed Linux PCs. Once every little incompatibility is costing a Dell engineer time the hardware suppliers will straighten their acts up fast!

---

### Post by ciborium on 2008-12-14
> **oilchangeguy said:**
> i did not toss the answer aside. i've tried various options, except for manual partitioning. and like i said, i may try this at some point. and i agree that there may be some kinks to workout. but these should arise after the os is installed. getting the os to install should be cut and dried. like i said if linux is ever going to appeal to the masses jumping through hoops to simply install the os should not be. what about the fact that most computer users barely know how to turn them on, let alone jump through hoops to install an operating system.


The masses don't custom build their own computers, or cobble them together from bits and bobs that have been salvaged.  Off the shelf systems are EXACTLY what the masses have and if the CD boots and installs on them, then Canonical have done their job.  Even Windows does stupid things if you don't plan your custom box for it.

You mean getting it installed like in Windows?
Check out all the cranky people at newegg.com complaining about the problems they have with motherboards and Windows, especially when they mix xyz memory with abc mobo's.

---

### Post by oilchangeguy on 2008-12-15
UPDATE!! I finally got it to install! I used the 80gb hard drive, and the mobo controller. The other two drives are disconnected. At some point I'm going to figure out the 200gb hard drive issues. I'll probably have to manually set the hard drive in the bios. At present they're set to auto. And show as 200 under Windows, and Kubuntu's live cd. However the grub 18 error shows up because under the auto setting it maxes out at less than 85000mb. So a 200gb hard drive using the bios auto setting drives linux insane. So another project, for another day.

Now if I can just get Sirius to play I'll be happy.

---

### Post by CatKiller on 2008-12-15
> **oilchangeguy said:**
> UPDATE!! I finally got it to install!

Glad to hear it.

---

### Post by oilchangeguy on 2008-12-16
I just got sirius to work!! Install the firefox add-on media player connectivity, and either mplayer, or vlc. I've got both and the default player is mplayer. Sign into sirius player and select your stream, and a little box will open and mouse over it and you'll be prompted to click to start. That's it!

---

