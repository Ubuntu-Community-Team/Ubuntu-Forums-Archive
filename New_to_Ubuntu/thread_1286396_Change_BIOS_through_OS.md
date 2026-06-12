---
title: "Change BIOS through OS"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Spencer Caplan on 2009-10-08
Is there any way to change the BIOS configuration while the OS is loaded? My laptop keyboard just stopped working and I need to change operating systems through a live CD. I can use a keyboard via a USB keyboard which I can plug in. But the computer is set to first boot from the hard drive and it doesn't allow the USB keyboard to work until after GRUB if finished loading. Therefore I can not simply press F2 before it boots because the keyboard won't work until after. Is there anyway to get the live CD to load?

---

### Post by ibuclaw on 2009-10-08
Try powering off, disconnect AC, remove the battery, press the power button, reinserting the battery, power it on.

May sound strange, but that resolved the issue the last time my lappy keyboard last stopped working.

Regards
Iain

---

### Post by |Mitch| on 2009-10-08
Not sure about the keyboard not working, but there is no way to change bios settings in the OS.

---

### Post by LinuxRocks9.04 on 2009-10-09
I'm not exactly sure what you're saying. Are both the BIOS and OS not recognizing keyboard input? If so, then the problem might be in the drivers the BIOS first loads.
The BIOS is accessed when the computer is turned on, so you can't change anything when the OS has already booted.

---

### Post by Spencer Caplan on 2009-10-09
> **LinuxRocks9.04 said:**
> I'm not exactly sure what you're saying. Are both the BIOS and OS not recognizing keyboard input? If so, then the problem might be in the drivers the BIOS first loads.
The BIOS is accessed when the computer is turned on, so you can't change anything when the OS has already booted.

The keyboard which is part of my laptop is physically not working at all. I have a USB keyboard which, when Ubuntu is running, does function. When the BIOS screen is loading, the USB keyboard does not work because the computer doesn't respond to the USB ports until the GRUB menu. For warranty reasons I need to use a Windows disc to reinstall XP. The computer automatically boots from the hard drive and I can not press F2 at the BIOS screen because the USB keyboard is not yet recognized. Do you have any ideas as to how I could reinstall XP?

---

### Post by aesis05401 on 2009-10-09
You need to find the default BIOS settings for your model.  If 'legacy USB support' is enabled in the default BIOS (And it often is), then resetting the BIOS according to manufacturer instructions can be attempted to allow USB keyboard interaction during boot.

---

### Post by aesis05401 on 2009-10-09
It occurs to me that if you have a floppy drive you could download freedos, download the latest DOS based BIOS image from the vendor and reflash the whole laptop - provided your floppy was on the boot menu.

Just a thought.  You can do the same with a bootable .iso but it sounds like the cd is not in the boot list.

---

### Post by Spencer Caplan on 2009-10-09
> **aesis05401 said:**
> It occurs to me that if you have a floppy drive you could download freedos, download the latest DOS based BIOS image from the vendor and reflash the whole laptop - provided your floppy was on the boot menu.

Just a thought.  You can do the same with a bootable .iso but it sounds like the cd is not in the boot list.

I do not have a floppy drive on my laptop. The cd is in the boot list, but the hard drive is listed first so it always goes to that by default. If I were able to wipe the hard drive so that there was no operating system on the drive, would it then go down the line in boot list items and check the CD? If so, how would I wipe the hard drive?

---

### Post by Spencer Caplan on 2009-10-09
> **aesis05401 said:**
> You need to find the default BIOS settings for your model.  If 'legacy USB support' is enabled in the default BIOS (And it often is), then resetting the BIOS according to manufacturer instructions can be attempted to allow USB keyboard interaction during boot.

How would I go about checking the default BIOS settings as resetting them?

---

### Post by LewRockwell on 2009-10-09
what is the make, model, and build/part number of the machine referenced in this trouble-call?

.

---

### Post by theozzlives on 2009-10-09
> **Spencer Caplan said:**
> The keyboard which is part of my laptop is physically not working at all. I have a USB keyboard which, when Ubuntu is running, does function. When the BIOS screen is loading, the USB keyboard does not work because the computer doesn't respond to the USB ports until the GRUB menu. For warranty reasons I need to use a Windows disc to reinstall XP. The computer automatically boots from the hard drive and I can not press F2 at the BIOS screen because the USB keyboard is not yet recognized. Do you have any ideas as to how I could reinstall XP?

Just remove the HD and send it in with a note stating that it contains sensitive data. The manufacturer will more than likely respect that, fix your keyboard, and send it back without a hard drive. They'll just use an XP HD while their working on it. I did that with my Dell.

---

### Post by Michaelg14 on 2009-10-10
If your laptop has a ps2(?) connector you can get a keyboard that plugs into it and does not need a driver to work.  That will be the simplest way to access BIOS

---

