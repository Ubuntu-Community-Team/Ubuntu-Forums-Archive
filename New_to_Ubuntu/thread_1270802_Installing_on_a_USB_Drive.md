---
title: "Installing on a USB Drive"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by CrimsonCasio on 2009-09-20
Hi, I'm very new to linux and I'm having a problem with installing ubuntu on a USB drive - or rather with how it operates after installation. The issue is that the computer I used for the install can no longer boot without the USB key plugged in (it has 3 other OS's on it, windows, an in-windows installation of ubuntu, and knopix on a SD card). The problem is with the Grub boot loader, which is at least partially on the USB drive(?), it starts to load then errors. So I guess my question is if there is a way to not use Grub, or if there is some other workaround to allow me to load my other OS's without having the USB key plugged in.

I also assume that my USB ubuntu wont work with other computers due to this, but I havent tried it yet. I also assume uninstalling will fix the problem, but then that leaves me without my porta-OS :(

Thanks for your help :)

---

### Post by superdav42 on 2009-09-20
Sounds like the bootloader got messed up on your HDD somehow. What happens when you try to but without the usb drive in? 

You can easily fix windows so it will boot by starting the recovery console from your windows installation disk and running fixmbr and fixboot.

---

### Post by CrimsonCasio on 2009-09-20
when I boot without the USB in, Grub starts to load then gives an error (I think #17 - cant check now) and I can only reboot. When I boot with it in, then select Windows in Grub, the Windows OS selection screen is displayed and I can choose between it and my other ubuntu installation (that is on the hard drive). Everything works fine with the USB in.

---

### Post by 3rdalbum on 2009-09-20
If you don't have a Windows installation CD, you can create a Windows Master Boot Record using the MS-Sys program ([http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)) on Ubuntu. This puts your computer back to only being able to boot Windows.

Unfortunately MS-Sys is not available in precompiled state anymore; you'll have to compile it yourself.

Then, you can follow a HOWTO about reinstalling GRUB, and this time make sure it gets installed to the USB flash drive and not to the hard disk.

---

### Post by CrimsonCasio on 2009-10-09
> **superdav42 said:**
> Sounds like the bootloader got messed up on your HDD somehow. What happens when you try to but without the usb drive in? 

You can easily fix windows so it will boot by starting the recovery console from your windows installation disk and running fixmbr and fixboot.

Ok, so I finally got around to trying this (been crazy busy). I've used fixmbr/fixboot before, but this time when loading the windows install CD I get a blue screen stop error. This occurs with and without the USB plugged in. Once I get some more time, probably tonight, I'll try creating a DOS boot disk and try that. I've never compiled anything, and have no idea how, so I'm reluctant to mess with that just yet - will a strait uninstall work? If all else fails, I'll just re-install.

Thanks for your help so far!

---

### Post by LewRockwell on 2009-10-09
> **CrimsonCasio said:**
> The issue is that the computer I used for the install can no longer boot without the USB key plugged in (it has 3 other OS's on it, windows, an in-windows installation of ubuntu, and knopix on a SD card). The problem is with the Grub boot loader, which is at least partially on the USB drive(?), it starts to load then errors.

When grub installed itself into your master boot record it pointed to your USB installation for the /boot/grub/menu.lst file...

There are several ways to fix:

One is to make the USB Ubuntu stick bootable and set your machine to boot first from USB devices

Another would be to put the /boot/grub/menu.lst file somewhere on the same drive your master boot record is on

> **CrimsonCasio said:**
> I also assume that my USB ubuntu wont work with other computers due to this, but I havent tried it yet. I also assume uninstalling will fix the problem, but then that leaves me without my porta-OS

You are most likely correct that the USB won't boot on it's own(although you can try it by setting your machine to boot from USB devices first)

If you wanted it to be a stand-alone self-contained USB Ubuntu system then you might look at:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

.

---

### Post by CrimsonCasio on 2009-10-09
> **LewRockwell said:**
> When grub installed itself into your master boot record it pointed to your USB installation for the /boot/grub/menu.lst file...

There are several ways to fix:

One is to make the USB Ubuntu stick bootable and set your machine to boot first from USB devices

Another would be to put the /boot/grub/menu.lst file somewhere on the same drive your master boot record is on



The drive is bootable, but I dont want my laptop dependent on me having my flash drive with me at all times to boot up. Booting with grub would be fine, I just dont want it to be dependent on me remembering to bring my drive everywhere (though it would be nice if it actually picked up any of my other OS's besides windows and the USB Ubuntu - still if I can get my USB working right I'll probably remove the on-board Ubuntu so it wont really matter).

Question though: Will moving the menu.lst file to a drive formatted for windows cause an issue? Also, do I need to point grub to the new location or will it figure it out (and if so, how do I do that)?


> 
You are most likely correct that the USB won't boot on it's own(although you can try it by setting your machine to boot from USB devices first)

If you wanted it to be a stand-alone self-contained USB Ubuntu system then you might look at:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

.

Thanks for the info, getting the laptop independent again is my first priority but once thats done I'll find the time to get the drive working :)

---

