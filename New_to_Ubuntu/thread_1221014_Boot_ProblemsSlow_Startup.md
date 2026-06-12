---
title: "Boot Problems/Slow Startup"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by .Masochist on 2009-07-23
Hi,

Recently I decided to dualboot Ubuntu  (9.04 Jaunty) and Vista on my HP (AMD Athlon 64 x2 dual core processor 4200+, 3.3Ram/(4 installed) with an empty partition of about 12gb. As far as I cna tell right now within Ubuntu it's working fine, but just this morning when I tried to startup my computer I have encountered some issues. 

When I first startup I get the blue HP screen that gives the key descriptions at the bottom (Esc for change boot order etc.), and starting from that screen I get a freeze of about 5-10 mins. Then it goes into the screen where I can pick which OS I want to go to. If I select Ubuntu it starts that loading screen with the bar, but in the middle it changes to a terminal like screen and gives a bunch of devices (IE "Bluetooth         [OK]") which I assume is part of the booting up process of the OS, but in the middle it starts giving about 10 or so error messages that say something like "usb 1-3: device descriptor read/64, error-110". Afterwards Ubuntu manages to startup at the desktop. 

When I first noticed the screen freeze I didn't think it would actually respond 10 mins later so I shutdown and put the live CD in, and booting the live CD had the same kind of weird boot errors. 

Yesterday when I booted Ubuntu I didn't have these problems, only this morning. So far I haven't noticed anything messed up. I don't know if this helps but the last time i started up with no error I went to the graphics and media thread to figure out how to get DVDs to play and installed a bunch of packages from that thread. 

Also, for some reason on the startup menu where you select the kernal(?) there are 5 ubuntu options, 2 of which say Ubuntu 9.04 and 2 of which say Ubuntu 9.04 (recovery). Is this abnormal? I thought there were only supposed to be one of each and the memtest thing? 

Sorry I have a hard time describing some of these issues as I am not tech savvy as most people here, but I would love to get Ubuntu working. 

Thank you for your help!

---

### Post by .Masochist on 2009-07-23
Bump

---

### Post by NightwishFan on 2009-07-23
Hello.

Firstly, I should ask to verify the CD you used to download. Just reboot and select the CD check. Please tell me if it passes.

Also make sure you do not have any bios boot issues. Make sure the correct disk is first in the boot order. As in behind other boot devices such as CDROM, which generally should be first in bios.

---

### Post by cariboo on 2009-07-23
From the error you are getting, it looks like you have a usb device that isn't functioning properly. Unplug an attached usb devices and reboot.

> Also, for some reason on the startup menu where you select the kernal(?) there are 5 ubuntu options, 2 of which say Ubuntu 9.04 and 2 of which say Ubuntu 9.04 (recovery). Is this abnormal? I thought there were only supposed to be one of each and the memtest thing?

The kernel has been updated, you have the option of using the new one or the previous version.

---

### Post by .Masochist on 2009-07-23
> **NightwishFan said:**
> Hello.

Firstly, I should ask to verify the CD you used to download. Just reboot and select the CD check. Please tell me if it passes.

Also make sure you do not have any bios boot issues. Make sure the correct disk is first in the boot order. As in behind other boot devices such as CDROM, which generally should be first in bios.

CD Check passed. Boot order is correct. 

> From the error you are getting, it looks like you have a usb device that isn't functioning properly. Unplug an attached usb devices and reboot.

I think this helped. I unplugged all my USB devices and the boot came in clean. I am still not sure how to fix this USB problem though; before the USB unplug I only had 1 device plugged in using a usb, which was my printer that had been functional. Along with that USB there were 2 cords plugged in but no devices to the ends of them (one for a cell phone and another for an ipod). 

> The kernel has been updated, you have the option of using the new one or the previous version. 	

Alright, that makes sense. How would I remove old kernels that I don't want (I assume in the future there will be more kernel updates and the list will begin to grow)? 

Anyways thank you both for your help I'll keep this thread updated if any other problems occur.

---

### Post by NightwishFan on 2009-07-24
There might be a bios setting to remove legacy USB settings or similar, you can play with that and see what works.

I have a similar problem with Fedora and OpenSUSE, only on them with a usb flash drive inserted, the vga mode of the console will not change so I get no boot splash.

---

### Post by lavinog on 2009-07-24
> **.Masochist said:**
> 
When I first startup I get the blue HP screen that gives the key descriptions at the bottom (Esc for change boot order etc.), and starting from that screen I get a freeze of about 5-10 mins. Then it goes into the screen where I can pick which OS I want to go to.
Since your problems start before reaching the grub menu, the problem can only be hardware related.
What brand printer is it?
Do you ever turn your printer off?
I have seen some printers act strange if they have been plugged in for long periods of time. (Most likely due to power fluxuations)
Also does your printer have a media card reader? Does your system boot differently if there is a card in it?

Also does your pc have a media card reader? These are usually connected to a usb header and can be prone to failure too.

---

