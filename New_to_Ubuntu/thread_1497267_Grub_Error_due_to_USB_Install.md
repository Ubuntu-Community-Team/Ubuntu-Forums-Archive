---
title: "Grub Error due to USB Install"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by Sethalos on 2010-05-30
So...I wanted to try the installation of Ubuntu on my USB drive...so I downloaded the installer, downloaded Ubuntu 10.04, installed it on my USB as per the instructions, and it worked great.

However, when I took out the USB and tried to boot Win 7 normally...I received a Grub error and cannot boot.

If I place the USB stick back into the computer and boot...I get the option to choose my loader.

What I need to do is to have my laptop boot normally into Win 7, and only when I place my USB stick into the computer have it offer to load Ubuntu.

Help!!

---

### Post by ajgreeny on 2010-05-30
Firstly boot to ubuntu on the external drive and then using the terminal run ```
sudo grub-install /dev/sdx
```where sdx is your usb disk, probably sdb or sdc, but if you don't know run ```
sudo fdisk -l
``` first, (that's a lower case L at the end).

That will put grub onto the usb drive and you will then need to restore the windows 7 boot loader with your win7 CD.  If you have no CD there are a number of utilities to do the same, but I am not sure about win 7, so you will need to find that from elsewhere.

Now if the usb is first boot device, and is attached, you will get grub and be able to chose the OS to use, if the usb is not present the system will go straight to windows.

---

### Post by Sethalos on 2010-05-30
Thanks much...I'll try this and post on the outcome.

---

### Post by Sethalos on 2010-05-30
Ok, followed the directions, and it did install the Grub on the USB (although I think that was already there as I could boot from the USB)...However, I still can't boot normally into my Win 7 from my laptop.

I booted the laptop using the Win 7 disk, went to repair, then chose Repair Startup ... and it says it can't find a problem.

However, it won't allow me to boot in as I get an error at the beginning saying it can't find such device, and the I get

> Grub Recovery (or something similiar in a console type thing)

Not sure how to repair my laptop so I can use it to boot normally again.  Also it says that the Win 7 is located on /dev/sda1  if that helps.



**Note: Love Ubuntu 10.04!!!!

---

### Post by ajgreeny on 2010-05-30
Sorry, others will need to help you with that; I got rid of windows a while ago, so have almost forgotten how to use it now, never mind fix problems with it.

---

### Post by Sethalos on 2010-05-30
Okies, thanks.

Anyone else able to fix the boot loader for Win 7?

---

### Post by Sethalos on 2010-05-31
I've done some searching around about this problem, but can't seem to find anything helpful.

I don't know if this is a Win 7 issue, or if it is a Linux issue as it started when I installed to USB....plus the error I'm getting is a grub error, so I'm sure that I have to fix this within linux.

I could reallllly use some help here folks...thanks much.

---

### Post by Sethalos on 2010-06-01
Anyone else that has this problem the answer lies here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Specifically paragraph 16:

```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

---

### Post by SRST Technologies on 2010-06-01
Installing LILO has nothing to do with fixing Grub errors from a USB install.  It does not fix Grub, it replaces it with LILO.  Who wants LILO these days, it is not as nice as grub is.

The easy fix would have been to set the USB disk as a later boot priority than the hard drive, then go into boot selection at the POST screen and choose to boot from the USB disk anyways.  F12 usually does this, consult your manual.  When you do it this way, it is forced to boot to USB but the HDD remains the first drive the BIOS sees, so it will install Grub to the HDD instead of the USB device.  Remove USB after installing this way, reboot, and you have a working system that does not require the USB disk to work right.

---

### Post by Sethalos on 2010-06-01
> **SRST Technologies said:**
> Installing LILO has nothing to do with fixing Grub errors from a USB install.  It does not fix Grub, it replaces it with LILO.  Who wants LILO these days, it is not as nice as grub is.

The easy fix would have been to set the USB disk as a later boot priority than the hard drive, then go into boot selection at the POST screen and choose to boot from the USB disk anyways.  F12 usually does this, consult your manual.  When you do it this way, it is forced to boot to USB but the HDD remains the first drive the BIOS sees, so it will install Grub to the HDD instead of the USB device.  Remove USB after installing this way, reboot, and you have a working system that does not require the USB disk to work right.

Well, I tried that and it didn't work at all. I also tried a number of other suggested fixes from friends and colleagues and they didn't work either.

However, I found the link (shown above) and booted into my livecd, ran the command, and boom....worked perfectly.

Keep in mind that I'm not talking about the usb install, I'm talking about my Windows 7 install on my laptop which somehow became corrupted when I installed Ubuntu onto the USB stick. I wasn't able to boot up my laptop with Win 7, as I received a GRUB error.

This fix worked for me, as well as another friend who had the exact same problem.

---

### Post by KhaiJB on 2011-01-16
> **Sethalos said:**
> Okies, thanks.

Anyone else able to fix the boot loader for Win 7?

here ya go

[http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html](http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html)

---

