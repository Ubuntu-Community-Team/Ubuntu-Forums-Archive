---
title: "Confused about USB boot"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by TomFulton53 on 2009-02-09
Just a warning: I am a thumb-in-the-mouth beginner to Ubuntu (although I am a software developer).

I got the 8.10 Ubuntu distribution on DVD in a magazine last week.  After a quick trial, I was very impressed, and wanted to install it to a USB stick.  I can't afford to install it to, or partition, my main drive at the moment, but I may be adding a removable drive soon.  I tried using the "Install to USB" option from the Live DVD desktop, but it crashed each time I tried to run it.  So in doing some additional research, I discovered a utility called "unetbootin" that would install an ISO image to a USB drive, so I downloaded the latest 64-bit ISO version and installed it to the thumb drive.  It worked, and I am able to boot to this 4GB USB drive.

However, it appears that this is just an image, for want of a better word, of the Live CD version.  In particular, I can't seem to save any of my settings.  This means that I can't (apparently) create a couple of user accounts, assign passwords to them, and have the system prompt for a password before it starts.  In addition, any settings to things like fonts, default web sites for firefox, etc, are not saved, and are reset each time I boot.

Does anyone have any suggestions about how I can use this 4GB thumb drive to run Ubuntu if the application to create a bootable USB drive crashes each time I run it?  Note: I tried both the 32-bit and 64-bit versions, and they both crashed (this is on a T61P Thinkpad running XP).  I even tried "installing" Ubuntu from the Live DVD to a different USB drive, 12GB in this case.  That also wouldn't work.  So I am confused how to proceed.  I am not familiar with Linux, so command-line commands are not going to go well (or have a much greater chance of messing up my system).

Thanks in advance.  I am really motivated to move on to Ubuntu and away from Windows (although I will still have to use it to run games) for most of my work.

---

### Post by unplugged23 on 2009-02-09
This website was extremely helpful when i did my USB installation.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by TomFulton53 on 2009-02-09
Thanks, unplugged.  I did see that article, but unfortunately it uses the same utility to create the USB stick that crashes each time I use it.

I may be in the situation that I simply can't use a USB boot from this machine, and will need to install Ubuntu to an actual partition.  But the reason I'm still trying is: I can actually boot Ubuntu from my existing USB, which means to me that it's possible.  It might be that the changes needed to make this a fully viable Ubuntu installation are more involved than I am capable of at my current stage of evolution:lolflag:!

---

### Post by unplugged23 on 2009-02-09
Hmmmm....
Is it worth it enough to you to go and by a portable pocket sized hard drive and install to that?

---

### Post by TomFulton53 on 2009-02-09
Yes, it might be worth it.  But the essential problem still remains: I need to install it to a USB device, as opposed to a partition that is part of the existing system.  If I can't get it to install to a 4GB thumb drive, I can't see how increasing the capacity to 400GB will make the installation suddenly work.

In addition, I am still uncertain about the long-term viability of Ubuntu as my development environment.  I'd rather rather buy a larger drive only after I've tested it out.  A lot of my development occurs when I travel, and it's easier to carry around a 4-16GB thumb drive than a larger drive.

---

### Post by avtolle on 2009-02-09
I've not installed on a USB thumb drive/flash drive or whatever the name *du jour* is. One thing I've noticed in reading various guides is that one needs to install in persistent mode to save changes. So, the ultimate question is did you install a persistent mode (I believe that is the name for what I'm trying to post on) when you did the installation on the USB drive?

EDIT: Does [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) give you any help?

---

### Post by MarblePanther on 2009-02-09
Boot the livecd and *install* it to the usbkey as if it were your harddrive partition (choose manual partitioning).  I don't mean the usb-installer.  When you boot the cd, choose install (not the live environment).  Just make sure you have your usb drive plugged in beforehand, and choose to install GRUB to the usb-stick afterwards.

---

### Post by unplugged23 on 2009-02-09
> **TomFulton53 said:**
> Yes, it might be worth it.  But the essential problem still remains: I need to install it to a USB device, as opposed to a partition that is part of the existing system.  If I can't get it to install to a 4GB thumb drive, I can't see how increasing the capacity to 400GB will make the installation suddenly work.

In addition, I am still uncertain about the long-term viability of Ubuntu as my development environment.  I'd rather rather buy a larger drive only after I've tested it out.  A lot of my development occurs when I travel, and it's easier to carry around a 4-16GB thumb drive than a larger drive.

Because you can mount this as a hard drive and do the installation as it were an actual hard drive, not a USB

EDIT: even though it technically is a USB

---

