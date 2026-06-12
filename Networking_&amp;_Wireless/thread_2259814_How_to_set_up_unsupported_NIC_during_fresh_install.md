---
title: "How to set up unsupported NIC during fresh install of Lubuntu"
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by Rising Eagle on 2015-01-07
Have a brand new HP Stream 13.3 with win 8.1. I don't even want to boot windows once. I just want to put lubuntu 15.04 on it and overwrite windows. However, the particular NIC is a Realtek RT-8723BE and is not in the installer's NIC list. None of the ubuntu installers have it. So, where can I get a linux driver and what do I do to prepare it before copying it onto my USB install drive? I'm using the advanced install option and choosing none in the NIC list which will allow me to configure a driver. However, without a driver, I can't even go through and find out what the config steps might be.

Some possible options
1 - I can get hold of a win driver and ndiswrapper. Can the installer accommodate a config process using ndiswrapper and a win driver?
2 - FLAME ALERT - I can't for the life of me understand why the developers make a full .iso and then not allow you to install without a network connection. It is always easier to work with a computer with a fully operating os to resolve problems then to mess around during the install process!
3 - does a live preview have a better chance of being able to set up network than the direct install?

Please help me avoid another win 8 apocalypse!


R. E.

---

### Post by kpatz on 2015-01-07
AFAIK you don't need a network connection to install Lubuntu.  It'll install from the USB provided you use a full install ISO as your source.

There is an option to download updates while installing, just uncheck this option and it should install without a network connection.

Try running the live version and see if you can get online.  If the live install can, the full install can as well.

---

### Post by ajgreeny on 2015-01-07
No need to worry about being online when you install; even when I can install with a connection I never let it update or install the third party packages as I prefer to do it myself later and just get the OS installed and running.

As kpatz says, simply untick the boxes for updating and third party apps when you get to that stage and let it continue; it will then probably be able to finish installing in about 15mins or maybe quicker.  Then once you have rebooted into the installed OS run the updates and other installations you need.

---

### Post by chili555 on 2015-01-07
The driver rtl8723be is included in Ubuntu 14.10 and following:```
/lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
```The required firmware is included in the most recent versions of linux-firmware which is installed automagically. I believe your NIC will work out of the gate.

Solved?

---

### Post by Rising Eagle on 2015-01-07
> **kpatz said:**
> AFAIK you don't need a network connection to install Lubuntu.  It'll install from the USB provided you use a full install ISO as your source..

There are only two .iso images for lubuntu 15.04: desktop and alternate install. I am using desktop and in all install options, the install gets stuck in an unbreakable infinite loop when it asks for a mirror site. Someone else reported the same problem with the alternate install.

> **kpatz said:**
> There is an option to download updates while installing, just uncheck this option and it should install without a network connection.

Cannot get this far!

> **kpatz said:**
> Try running the live version and see if you can get online.  If the live install can, the full install can as well.

As for live install, the desktop .iso doesn't seem have that option (or else I don't know how to invoke it).

---

### Post by Rising Eagle on 2015-01-07
> **ajgreeny said:**
> No need to worry about being online when you install; even when I can install with a connection I never let it update or install the third party packages as I prefer to do it myself later and just get the OS installed and running.

It gets stuck in an infinite loop at the mirror site selection and won't let me go further. If you know a way around it that could be the key.

---

### Post by kpatz on 2015-01-07
15.04 is still in development, so it is updated frequently.  Perhaps the iso needs a network connection to download the latest packages when installing.

Is there a reason you're installing 15.04, instead of 14.04 LTS or 14.10?  Those should be able to install without a network connection, and you can run them as a live CD for testing as well.  They're also stable, while 15.04 is in alpha and likely still has bugs.

---

### Post by Rising Eagle on 2015-01-07
> **chili555 said:**
> The driver rtl8723be is included in Ubuntu 14.10 and following:```
/lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
```The required firmware is included in the most recent versions of linux-firmware which is installed automagically. I believe your NIC will work out of the gate.

Solved?

This sounds promising, I wonder why it is missing in the lubuntu 15.04 installer NIC list. Do you know where I can download it?

---

### Post by Rising Eagle on 2015-01-07
> **kpatz said:**
> 15.04 is still in development, so it is updated frequently.  Perhaps the iso needs a network connection to download the latest packages when installing.

Is there a reason you're installing 15.04, instead of 14.04 LTS or 14.10?  Those should be able to install without a network connection, and you can run them as a live CD for testing as well.  They're also stable, while 15.04 is in alpha and likely still has bugs.

Mostly knowing I have latest and greatest. Also, I always felt that the last remaining unfinished blueprints from a release are addressed early in the following release's development. However, your point is valid; I should set feelings aside and try a stable release.

---

### Post by chili555 on 2015-01-07
> I should set feelings aside and try a stable release.I agree. I did a clean install of 14.10 on this very computer several months ago. It recognized my wireless right from the start.> missing in the lubuntu 15.04 installer NIC list. I have never seen this. I wonder if it is new for 15.04.

---

### Post by Rising Eagle on 2015-01-08
> **chili555 said:**
> I agree. I did a clean install of 14.10 on this very computer several months ago. It recognized my wireless right from the start.I have never seen this. I wonder if it is new for 15.04.

I have met with complete success, so I will share some lessons learned:

1 the HP stream 13.3 (a win8 competitor to a chromebook) is fully compatible with lubuntu 14.10
    this version uses kernel 3.16 which has the real tek drivers, whereas earlier kernels (3.13) from earlier ubuntus are  buggy and/or completely
    incompatible with these drivers (and so do not have them at all)
2 unetbootin (at least the older version of it that I used) will create a bootable usb,
    although even using and UEFI .iso, the usb created will only actually boot in legacy bios mode
3 ubuntu startup disk creator is deadbeat software and always fails to complete the usb (even when run as root)
4 interestingly, deleting the folders created by startup disk creator on the usb (leaving the random root level files in place on the usb) and then
    using unetbootin will create a bootable usb that will boot in UEFI mode
5 the live boot of lubuntu with a  "UEFI" usb from unetbootin that will only actually boot in legacy bios mode will install lubuntu as bios compatible
     but on reboot presents a UEFI grub that allows you to install lubuntu a second time which creates a fully UEFI compatible installation
5.1 a fully UEFI compatible usb that is actually booted in UEFI mode will install a fully UEFI compatible lubuntu by default
6 the live boot lubuntu allows one to install without a network connection
7 boot times (with login set to automatic and login screen automatically bypassed) is 20 sec from power button to desktop on clean UEFI install
8 shut down is 6 sec from enter to power button light goes out
9 lubuntu 15.04 is not ready for prime time as it has has no live boot option, is missing some network drivers, and runs an infinite loop when not connected
10 never did learn how to configure a network driver for an install usb that lacks the one needed because 14.10 already had the driver I needed
     and it would be nice if someone made a tutorial with step by step examples
11 to invoke bios screen on the HP stream 13.3, one must press power on and immediately begin tapping f10 quickly, over and over until the screen shows
12 if the usb is fully UEFI compatible, bios screen is not needed, press power on and immediately begin tapping f9 quickly,
      over and over until a boot device select menu shows

Thank you everybody for your help. This case is closed.

R. E.

---

