---
title: "[SOLVED] Need to boot from CD"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by gener9 on 2008-12-03
I installed Ubuntu 8.10 on a friend's old Compaq hoping to avoid problems with Windows.  However the modem is not recognized and dial-up is the only internet option.  I need to reinstall Windows but cannot find out how to boot from a CD.  Please help.

---

### Post by Titan8990 on 2008-12-03
Should be able to bring up a boot menu or alter the boot order in the BIOS. Did you boot to a CD when you installed Ubuntu?

---

### Post by kernel tom on 2008-12-03
I believe for Compaq you hit F12 when you see the initial manufacturer's logo on your machine, you can hit it a few times if you're unsure when to.  This should bring up the 1 time boot menu which you can select boot from CD/DVD drive.

-kt

---

### Post by Michael.Godawski on 2008-12-03
To boot from a CD you first have to make sure the Bios settings are correct. After a restart there should be a messages which tells you which key combination opens up the bios setup. The usual combinations are : Del or f2. But it differs from machine to machine.

When you are in the Bios setup there search for the boot device order. Select the CD-Rom as the first one followed by the drive. (or a floppy :p) Quit and save, and if you cd-rom is working the next start should boot from the cd.

---

### Post by cartisdm on 2008-12-03
This is kind of a lazy way but I just run my finger along the top row of Function keys when I'm on a new computer and don't know the Boot To function.  :) It usually throws me into the BIOS though but that's fine because you just tell it to boot to CD first.

Generally it's F8, F10, or F12 though

---

### Post by gener9 on 2008-12-03
Thanks for the replies but I have been trying to get to BIOS using the function keys.  I've tried them all but I recall F2 used to work in Windows and I know it was set to boot from CD first.  The CD is working because I used it to install Ubuntu and I can see the Windows install disk on the desktop.  I thought maybe I'd have to change a config file or something.  Thanks again for your time.

---

### Post by oilchangeguy on 2008-12-03
> **gener9 said:**
> Thanks for the replies but I have been trying to get to BIOS using the function keys.  I've tried them all but I recall F2 used to work in Windows and I know it was set to boot from CD first.  The CD is working because I used it to install Ubuntu and I can see the Windows install disk on the desktop.  I thought maybe I'd have to change a config file or something.  Thanks again for your time.

the operating system has nothing to do with being able to enter the bios. you're not pressing the right key. may be the del key. anyway, shutdown the computer. press and hold the esc key, start the computer. you'll get a keyboard error, and be prompted to enter the bios. then confirm the boot order.

---

### Post by Duck2006 on 2008-12-03
> **oilchangeguy said:**
> the operating system has nothing to do with being able to enter the bios. you're not pressing the right key. may be the del key. anyway, shutdown the computer. press and hold the esc key, start the computer. you'll get a keyboard error, and be prompted to enter the bios. then confirm the boot order.

If all else fails this should work.

---

### Post by theozzlives on 2008-12-03
> **gener9 said:**
> I installed Ubuntu 8.10 on a friend's old Compaq hoping to avoid problems with Windows.  However the modem is not recognized and dial-up is the only internet option.  I need to reinstall Windows but cannot find out how to boot from a CD.  Please help.

I can't get my modem on my old Compaq also but I have Broadband, your friend might wanna think about either that or an external modem.

---

### Post by gener9 on 2008-12-03
I just tried that but didn't get the keyboard error message.  However Cartisdm's suggestion did work and I got into BIOS but the boot order does list CD first, floppy second and hard drive last.  The CD light flashes like it's loading but then Ubuntu boots from the hard drive anyway.  I tried inserting the Ubuntu 8.10 install disk because I know it's bootable and it was bypassed too.  The Windows install disk will boot my computer (a new Dell laptop) so I know it's not a bad disk.  I am stumped.

---

### Post by theozzlives on 2008-12-03
> **gener9 said:**
> Thanks for the replies but I have been trying to get to BIOS using the function keys.  I've tried them all but I recall F2 used to work in Windows and I know it was set to boot from CD first.  The CD is working because I used it to install Ubuntu and I can see the Windows install disk on the desktop.  I thought maybe I'd have to change a config file or something.  Thanks again for your time.

Windows displays a brief message saying, "Press a key to boot from CD...". Look for that.

---

### Post by Michael.Godawski on 2008-12-03
Let's summarize:

Your Windows CD is not corrupt, because you can boot from it on another machine.

Your Ubuntu CD is not corrupt, because you have installed Ubuntu with it, without any troubles.

When you log in into Ubuntu, the CD-ROM is working because it sees the Windows CD as well as the Ubuntu CD.

The boot order in BIOS is correct.

But can a linux installation render a system completely unable to boot from a CD?

---

### Post by oilchangeguy on 2008-12-03
> **gener9 said:**
> I just tried that but didn't get the keyboard error message.  However Cartisdm's suggestion did work and I got into BIOS but the boot order does list CD first, floppy second and hard drive last.  The CD light flashes like it's loading but then Ubuntu boots from the hard drive anyway.  I tried inserting the Ubuntu 8.10 install disk because I know it's bootable and it was bypassed too.  The Windows install disk will boot my computer (a new Dell laptop) so I know it's not a bad disk.  I am stumped.

dead cd drive. do you have another one you can test with?

---

### Post by gener9 on 2008-12-03
> **oilchangeguy said:**
> dead cd drive. do you have another one you can test with?

I don't think the CD drive is dead because I can open folders in the Windows install disk and the Ubuntu install disk.  However, in each case I don't see the autorun files.  I do see them on my computer.  I tried starting the setup file in Windows but Ubuntu won't run it.  We don't have another CD drive to use and spending money on broadband or a new modem is not affordable for my friend who is retired and barely gets by.  I gave him the old Compaq a few years ago just so he could keep in touch with family.  I recently upgraded him from Windows 98 to XP Home but it ran so slow and used up so much disk space the computer was almost unusable.  I thought Linux would be a good alternative and researched Ubuntu but somehow missed that it didn't support most modems.

---

### Post by Titan8990 on 2008-12-03
I have had this issue before on my school's computer. You have to use some kind of other bootable media to remove grub from the MBR. I think it has to do with poorly made BIOS on pre-built computers.

---

### Post by Duck2006 on 2008-12-03
> **Titan8990 said:**
> I have had this issue before on my school's computer. You have to use some kind of other bootable media to remove grub from the MBR. I think it has to do with poorly made BIOS on pre-built computers.

Can be done from with in ubuntu or if it works the live cd.
This shows how to do it from the live cd, but you can do it from with in ubuntu.

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by gener9 on 2008-12-03
> **Duck2006 said:**
> Can be done from with in ubuntu or if it works the live cd.
This shows how to do it from the live cd, but you can do it from with in ubuntu.

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

I just looked at this link but it says to boot into the Ubuntu CD and it won't boot either.  On bootup my CD is being ignored.  When Ubuntu starts, the first line of config code I see is:  Boot from (hd 0,0) ext3 followed by a long string of characters.  I was hoping maybe that could be changed to CD.  I forgot to mention that when I try to boot from CD I get a desktop message after startup that says:  This medium contains software intended to be automatically started.  Would you like to run it?  If I select run I get this message:  Error running software.  Cannot find the autorun program.  I hit OK and it goes back to desktop.

---

### Post by Duck2006 on 2008-12-03
Can you boot to the installed system on the hard drive?

---

### Post by gener9 on 2008-12-03
> **Duck2006 said:**
> Can you boot to the installed system on the hard drive?

Ubuntu boots perfectly from the hard drive.  If you're talking about Windows I can't find any sign of it.  I did not do a dual install but let Ubuntu partition and format the harddrive and start all over because the documentation said it would run faster this way.  But 2 GB of the hard drive seems to be unaccounted for and that's about how big the Save drive was under Windows.  If I could locate that it may be possible to restore Windows.

I have to leave this problem for a few hours but will check back later.  Thanks so much for your time and interest.  I know it seems trivial and cheap but I'm just trying to keep an old friend connected.

---

### Post by Duck2006 on 2008-12-03
You can fix your mbr from with in ubuntu with the link i gave you. Then see if you can boot to windoze. if not partition the drive with gparted or parted magic, and see if you can boot in to windoze cd dvd. Then you can reinstall grub and add windows to your menu.lst
Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by gener9 on 2008-12-04
> **Duck2006 said:**
> You can fix your mbr from with in ubuntu with the link i gave you. Then see if you can boot to windoze. if not partition the drive with gparted or parted magic, and see if you can boot in to windoze cd dvd. Then you can reinstall grub and add windows to your menu.lst
Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

It appears that I was dealing with an intermittant CD drive problem.  Last night I was able to boot from the Ubuntu CD and I tried to follow the instructions in the link.  Here's what happened:

1.  When I entered "sudo apt-get install ms-sys" it responded 
"couldn't find package ms-sys".
2.  When I entered "sudo fdisk -l" it responded with several columns.  The Device Boot column lists /dev/sda1 *, /dev/sda2, /dev/sda5.  The System column lists Linux, extended Linux swap/Solaris.

So it seemed to me that Windows no longer exists on the hard drive and I couldn't pursue the solution any further.  Since the Ubuntu CD booted I tried the Windows Install CD but it still wouldn't boot.  The Ubuntu CD wouldn't boot when I tried it again either.  At this point I decided that the CD drive must be suspect.  Another old friend has a PC about the same age that he has been using for parts so I bought his CD drive and hard drive for $10 and installed them and upgraded the existing Windows 2000 operating system to XP home.  Right now the old Compaq is running slow as before but it is running.

I want to thank everyone who made suggestions to solve this problem.  I am seriously considering switching my new computer to Ubuntu because even though I've used Windows for years and am comfortable with it, I hate the BS you have to put up with.  I am going to research Ubuntu much more thoroughly before I make a decision but the responses I received in this forum make me think it might be the right decision.

---

