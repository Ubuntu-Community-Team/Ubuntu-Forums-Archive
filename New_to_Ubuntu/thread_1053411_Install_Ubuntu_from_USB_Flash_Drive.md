---
title: "Install Ubuntu from USB Flash Drive"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by F4rrari on 2009-01-28
Hi,

I have a laptop that I want to load Ubuntu but unfortunately, my CD-ROM is Bad. Is there anyway to put the CD onto the USB Flash Drive so I can load it onto my laptop without using the CD?
My Laptop does support bootup from USB Flash Drive.

---

### Post by UnknownFear on 2009-01-28
[http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php](http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php)

If this isn't helpful, you can actually install Ubuntu on a Flash Drive right from Ubuntu. Go to System > Administration > Create a USB startup disk.

---

### Post by Therion on 2009-01-28
See this tutorial:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Unetbootin makes this operation a cakewalk.

---

### Post by Captain_tux on 2009-01-28
> **UnknownFear said:**
> If this isn't helpful, you can actually install Ubuntu on a Flash Drive right from Ubuntu. Go to System > Administration > Create a USB startup disk.
 
That is absolutely correct, but the functionality only currently exists on Intrepid... you'll be out of luck if you want to install Hardy.

---

### Post by F4rrari on 2009-01-28
Thank for the Reply, but those instruction is for installing Ubuntu onto USB Flash drive. I need info on loading Ubuntu from Flash Drive onto my Laptop Hard Drive which has Windows XP that I want to format.

---

### Post by F4rrari on 2009-01-28
Thank you all. Problem solved.

---

### Post by lauraannq on 2009-01-29
i set up the flash drive with the .iso to boot.  and it runs... can i just use it this way or do i need to 'install' it for it to work correctly.


this is my first time using a flash drive as a 'disk'

i am doing this so someone else can run ubuntu and learn to use it.

thanks

---

### Post by NewUser101 on 2009-04-15
> **F4rrari said:**
> Thank you all. Problem solved.

Hello everyone, first time post here!

I am fighting this same issue. In a nutshell, I got an older emachine (T3985) with no hard drive and no recovery disk. I put a 80 gig HD from a different machine into it, and have a restore disk for an ever earlier emachine (T2862) that when I boot from I can get it to recognize a flash drive. I would like to do a full ubuntu install on this machine but just copying the 8.10 ISO CD image to a folder does not do anything when I try to open it. 

I've tried a few other things of course, I have an external USB drive that it does not recognize so that is out. When I boot from the emachine disk and go into emergency restore and then remove the disk and replace it with the ubuntu disk it cannot read any other disk. I tried both ubuntu and an older version of XP install disk and it does not appear to read anything. Hopefully that makes sense! 

The only thing that I have not tried yet is taking everything off my flash drive (2 gig) and making it bootable. I have a bunch of applications on it so I'd rather not do that unless I have to.

Thanks for reading this far!

NewUser

---

### Post by digitalmonk on 2009-04-15
This time I installed jaunty beta from a flash drive. earlier i was using intrepid, downloaded the .iso from one of the mirrors, used the administration -> usb startup disk creator to load the .iso file on the usb drive.
then while booting i seleted the usb drive as the first boot device and installed jaunty.
it was pretty easy.however after the installation is over, please perform a full update including the pre-release updates.

---

### Post by NewUser101 on 2009-04-16
Thanks for the reply Monk, however I only have PC machines here and it sounds like you are setting it up in ubuntu or mac already. Is there a simple PC based program I can set this up with?

Thanks!

---

