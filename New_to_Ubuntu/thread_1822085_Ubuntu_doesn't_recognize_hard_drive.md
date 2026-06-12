---
title: "Ubuntu doesn't recognize hard drive"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by tehcavil on 2011-08-10
Hey I recently built a computer from parts I ordered off newegg.com

I decided to go with Ubuntu instead of windows this time as I'm studying computer programming at college and I heard Linux was better for people who wanted to program or learn how to program. 

I also liked the fact that it was free.

However I'm having some problems. I finally got it working (sort of) just now and am running Ubuntu 11.04 GNU/Linux off the live CD. However, Ubuntu is telling me there is no hard disk detected, which obviously is stopping me from installing the system.

The Hard drive is this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145520](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145520)

HITACHI Deskstar 7K3000 HDS723015BLA642 (0F12114) 1.5TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive

The specs of the system are:

[SIZE=1]Motherboard:
GIGABYTE GA-990FXA-UD5 AM3+ AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard

Power Supply:
hec Orion XPOWER585 585W ATX12V 2.01 Power Supply

CPU:
AMD Phenom II X6 1100T Black Edition Thuban 3.3GHz, 3.7GHz Turbo 6 x 512KB L2 Cache 6MB L3 Cache Socket AM3 125W Six-Core Desktop Processor

Memory:
G.SKILL Ripjaws Series 16GB (4 x 4GB) 240-Pin DDR3 SDRAM DDR3 1066 (PC3 8500) Desktop Memory

Graphics Card:
Visiontek Radeon 5450 2gb ddr3 memory[/SIZE][SIZE=1]

-----

Conclusion: There are one of three things happening.

1) The Hard drive works, but isn't recognized by Ubuntu

2) I plugged the hard drive in wrong

3) The Hard drive was DOA (as things ordered off newegg often are).

---

Please if anyone could tell me whether or not that particular hard drive is supported by Ubuntu or has had a similar problem or solution please inform me. :)

Thanks, Cavil.

-=-=-=-==-=-=-=-

EDIT: Issue Fixed.

Solution: I had to mess with integrated peripheral settings in BIOS. The mobo's default setting for all the sata ports including the 6.0 gb/s ones were IDE.

Unfortunately this hard drive only works with RAID or AHCI (I opted for the latter).

You have to go under integrated peripherals -> on chip settings ->

And switch the 6.0 gb/s ones from IDE (the default setting) to RAID or AHCI.

i guess if you wanted to use the regular ports for hard drvies. you could switch those from ide to another setting too.
[/SIZE]

---

### Post by Grenage on 2011-08-10
> **tehcavil said:**
> Please if anyone could tell me whether or not that particular hard drive is supported by Ubuntu or has had a similar problem or solution please inform me. :)

Thanks, Cavil.


Hard drives aren't generally unsupported - they should all work.  As this is a new build, have you rules out a configuration error?  Be it cables or BIOS options, something isn't right.  While the drive could be dead, it's rather unlikely, and you can test that elsewhere.

---

### Post by moody_mark on 2011-08-10
Check your BIOS, is the device listed in there? If not its likely the jumper settings on the drive may be wrong, you may need to tell the BIOS to search for the drive too. Start here, once its listed then you should be able to see the drive in Ubuntu.

---

### Post by YesWeCan on 2011-08-10
After you have confirmed it is shown in the bios,
please run:
[COLOR="Navy"]sudo sfdisk -luS[/COLOR]
and post the output here.

Is the disk brand new?

---

### Post by dcsoldschool53 on 2011-08-10
Check your BIOS. I took some snapshots from a part of your manual (I Think it was your motherboard manual from Gigabyte.com). Look and see if your hard drive is detected there. If you see the word none, change it to auto, so that your system can automatically detect your SATA drive.

**I hope this will help you out some.**

---

### Post by Mark Phelps on 2011-08-10
My Gigabyte motherboard and setup is similar to yours -- in that I too have a 6GB/s SATA drive, and it's connected to one of the two special SATA ports on the motherboard.

But the difference is, I'm NOT using this drive for Ubuntu.  Why? Because Ubuntu can't see the drive.

I think it's a driver problem with Ubuntu, the faster drives, and the new SATA ports.  You may have to connect it to one of the SATA 2.0 ports to get it recognized.

---

### Post by YesWeCan on 2011-08-10
In my ASRock bios I had to set the 6GB/s SATA to "bootable" and this caused the bios to load the drivers just after the POST before the option to select to boot off CD. Slows the boot down a bit.

---

### Post by tehcavil on 2011-08-10
The drive is listed in the CMOS Setup Utility as:

"Hitachi HDS723015BLA"

With the heading "IDE Channel 2 Slave".

I tried typing in [COLOR=Navy]sudo sfdisk -luS
[/COLOR]
in the terminal but there was no output.
It just made another prompt line.

So i know the BIOS sees it but not Ubuntu.

---

### Post by cgilbert16 on 2011-08-10
If you are running from the CD in live mode then it may be an issue with the system not being up to date.  Try (if you have enough RAM to do it) running
 sudo apt-get upgrade
 sudo apt-get update

These updates will be stored in the RAM.  I had an issue with some hardware testing I was doing from a live CD and that fixed it.

I am aware this is not technically an OS issue but the updates may help.  You could also run a killdisk on the drive just to make sure it does not have a file system on it already that Ubuntu does not recognize.  Check the system to see if it sees the drive at all at a hardware level.

---

### Post by dcsoldschool53 on 2011-08-11
[quote=tehcavil]With the heading "IDE Channel 2 Slave".[/quote]I thought that you said that you only had only one hard drive in your system. This says that you have an IDE drives on channel 2 and it's a slave device. Re-check your connection on your motherboard. I think that you may have plugged it in wrong. Tell us how you have yours connected.

With one hard drive, it should be the master, not the slave, and (I think) it should be on channel 0.

---

### Post by tehcavil on 2011-08-11
> **dcsoldschool53 said:**
> I thought that you said that you only had only one hard drive in your system. This says that you have an IDE drives on channel 2 and it's a slave device. Re-check your connection on your motherboard. I think that you may have plugged it in wrong. Tell us how you have yours connected.

With one hard drive, it should be the master, not the slave, and (I think) it should be on channel 0.

There are 6 sata ports on the mobo all together like in the picture you have attached and 2 slightly above that. The drive is plugged into one of those 2 above ones. 

The L-shaped part of the cable is attached to the drive while the other end is plugged into the board. The only other wire going from my drive is the power cable connected to the power supply.

---

### Post by dcsoldschool53 on 2011-08-11
Look in your motherboard manual. It should provide a clue to how you should be setup the hard drive. It is not the power supply.

---

### Post by tehcavil on 2011-08-12
> **dcsoldschool53 said:**
> Look in your motherboard manual. It should provide a clue to how you should be setup the hard drive. It is not the power supply.

OK I tested the hard drive in another computer so the hard drive itself works however the BIOS in mine still only sees it as an IDE channel 2 slave.

Should I try to update the bios firmware or is that not the issue? It's a brand new mobo so it should be compatible with all hard drives right?

---

### Post by Johnb0y on 2011-08-12
> **tehcavil said:**
> Should I try to update the bios firmware or is that not the issue? It's a brand new mobo so it should be compatible with all hard drives right?

Yes - update! ;)

---

### Post by YesWeCan on 2011-08-13
> **tehcavil said:**
> There are 6 sata ports on the mobo all together like in the picture you have attached and 2 slightly above that. The drive is plugged into one of those 2 above ones. 

The L-shaped part of the cable is attached to the drive while the other end is plugged into the board. The only other wire going from my drive is the power cable connected to the power supply.

Use one of the group of six. The others use Marvell chips and if my experience is anything to go by the bios needs to be deliberately configured to enable the Marvell during POST to be available to the Ubuntu installer.

---

### Post by tehcavil on 2011-08-14
[SIZE=1][/SIZE]Problem solved. See my original post I edited to see conclusion.

---

