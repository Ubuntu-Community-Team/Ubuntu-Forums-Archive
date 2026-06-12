---
title: "GParted will not open!"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by racie on 2010-05-24
Okay, so I'm struggling to try to format my SD card to FAT16 (FAT).  I tried to get it to mount with this command:
```
sudo mount -f FAT32 /dev/mmcblk0p1
```

I did not receive any errors afterward.  However, when I click on GParted under System > Administration > GParted, nothing loads.  It doesn't even start up.  I have tried uninstalling and reinstalling.  I feel like there is probably a simple explanation to this. :/  Thank you for your help!

---

### Post by SRST Technologies on 2010-05-24
Don't put your SD card in before you boot.  After you're logged in, insert the card.  It should appear on your desktop.  Right click the icon on your desktop for your SD card and select Format.

---

### Post by racie on 2010-05-24
It does not appear on my desktop.

*edit* Nevermind, my SD card just decided to be a bit cranky.  It shows up now.

*edit2* Err... It disappeared again.  I'm confused.

*edit3* GParted now appears, but is in a seemingly endless scan.  Please help!

---

### Post by SRST Technologies on 2010-05-25
I'd suspect either a bad SD card or a bad reader right now, or even that the SD Card Reader is drawing a lot of power from the USB bus and that you have a lot of other USB devices plugged in as well.  If you have a lot of other USB devices plugged in while the card reader is trying to be used, unplug what you can (you can even unplug a USB keyboard while doing this because you only really need a mouse to do this), then when you are done formatting plug it back in.

If this solves it, buy an addon USB PCI adapter, install it, and migrate some of your USB devices to that USB device to distribute the load and allow for less power consumption per USB device.

If that doesn't solve it, the cheapest way to test it first is to buy another SD card.  If that too does not work, then it must be your card reader, which is going to cost more than an SD card so be sure to try the new SD card first.

Good luck.

---

### Post by Don1500 on 2010-05-25
> **racie said:**
> It does not appear on my desktop.

*edit* Nevermind, my SD card just decided to be a bit cranky.  It shows up now.

*edit2* Err... It disappeared again.  I'm confused.

*edit3* GParted now appears, but is in a seemingly endless scan.  Please help!

Gparted can take a while to scan all your drives. Specially if you have a cd or floppy inserted.

Also, if you want to format your SD card, it should not be mounted.

---

### Post by SRST Technologies on 2010-05-25
The desktop icon will unmount anything that appears on the desktop while it formats, then will automount it again when done.

---

### Post by racie on 2010-05-29
Thank you everyone.  However, I think that SRST Technologies is right when he said it may just be a bad SD card.  Thanks anyway.  Guess I'll have to get a new one.  :/

Oh, GParted works when I take out the SD card.

---

