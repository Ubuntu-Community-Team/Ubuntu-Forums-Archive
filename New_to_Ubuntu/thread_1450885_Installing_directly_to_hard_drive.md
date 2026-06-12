---
title: "Installing directly to hard drive"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by nickjbanks on 2010-04-09
I'm trying to install ubuntu to a small PC. I can boot from a USB flash drive if no other drives are present but as soon as I plug a hard drive in it wants to boot from that. I've played with the bios and boot settings and it wont play so I want to try and set the hard drive up so it can boot from it. Is this possible? I've got a usb caddy for the drive. Thanks.

---

### Post by norm7446 on 2010-04-10
It's your BIOS that controls how your system boot's. Why not set your CD/DVD drive as the first boot, then run Ubuntu as a Live CD, then when you get onto the Desktop click on the install button. When this is finished if you have set the Hard Drive as the next boot option in the BIOS, the system will re-boot, eject the Ubuntu disc, and then boot from your freshly installed Ubuntu Installation on your Hard Drive. Simples  Squeak...

---

### Post by J V on 2010-04-10
Also, it is possible (But unwise) to plug in a hardware harddrive after the computer has been turned on/booted, shoulden't cause any damage if you have booted from usb, and should allow you to boot from harddrive.

But like norm said, better to use the bios first...

---

### Post by nickjbanks on 2010-04-11
Thanks for the replys. I've played with the bios settings and changed the order. The problem is that it boots fine from usb unless there is a hard drive plugged in then it will only boot (or rather nor boot) from that. I might try hot swapping the hard drive, bit wary of damaging the motherboard, the drive is scrapable, though.

---

### Post by Doctor Mike on 2010-04-11
> **nickjbanks said:**
> Thanks for the replys. I've played with the bios settings and changed the order. The problem is that it boots fine from usb unless there is a hard drive plugged in then it will only boot (or rather nor boot) from that. I might try hot swapping the hard drive, bit wary of damaging the motherboard, the drive is scrapable, though.
There's also likely a function key F(1..12) during initial boot that will allow boot drive selection.

---

### Post by jvc26 on 2010-04-11
nickjbanks: It's worth noting that some BIOSs require you to select the drive order for harddrives, there may be an option in your Boot Order selection screen which allows you to select harddrive order. If this is the case, go on there with the usb stick and the internal HDD plugged in and move the usb stick above the internal.

Il

---

### Post by nickjbanks on 2010-04-12
> **Illuvator said:**
> nickjbanks: It's worth noting that some BIOSs require you to select the drive order for harddrives, there may be an option in your Boot Order selection screen which allows you to select harddrive order. If this is the case, go on there with the usb stick and the internal HDD plugged in and move the usb stick above the internal.

Il

Yeah, that's what I had to do on my laptop. I don't have that option on this PC. I'm sure I'm missing an option somewhere but I've tried every menu and sub-menu.

---

### Post by norm7446 on 2010-04-12
To gain access to the BIOS, you normally only have a few second on initial boot to actually get into the BIOS window. Normal keys are F2, F8, F12, and the delete key. Try pressing them one at a time or if you cant wait and you are ambidextrous, you could try pressing them all at once.

---

### Post by quadproc on 2010-04-12
> **nickjbanks said:**
> Thanks for the replys. I've played with the bios settings and changed the order. The problem is that it boots fine from usb unless there is a hard drive plugged in then it will only boot (or rather nor boot) from that. I might try hot swapping the hard drive, bit wary of damaging the motherboard, the drive is scrapable, though.
If you post the make and model of your motherboard and/or the BIOS then someone may know exactly what you need to do to get the BIOS to boot from the desired device.

I am running an ASUS P6T SE and it needs the F8 key right after the BIOS finishes its power on sequence.  This is completely undocumented by ASUS; I had to call them to learn it.  ASUS does document the DEL key but it doesn't give access to the "drive selection" menu.

Plugging or unplugging a hard drive on a powered up system is risky.

quadproc

---

### Post by J V on 2010-04-12
From what you've said I suggest booting from the USB while the HD is physically disconnected, then reconnecting it.

Unplugging a mounted powered drive is indeed very risky (Actually you are begging for drivepocalyps)

Plugging in however should have the same effect as a usb stick. Not on windows, on windows it fscks up...

I have plugged/unplugged over 100 cd/dvd/hd/sd drives in this fashion.

Dirty hack but its easier than us trying to explain how to setup the bios

But on the other hand, if you have physical access to the HD anyway, just stick it in another computer and install from there. Then reprofile grub when you boot on the lappy and voila...

---

### Post by nickjbanks on 2010-04-13
Thanks for all the replys. I've just tried it with a different brand of usb stick and it worked. Odd as the first stick boots fine with the hdd disconnected, but there you go. Its installing now so I'm sure there will be some more questions coming soon :)

---

### Post by norm7446 on 2010-04-13
Congratulations. My I take this opportunity to welcome you to Ubuntu.

---

