---
title: "Keyboard + Mouse don't work"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by mayagrafix on 2010-05-17
Updated to 10.04 LTS from previous version and during boot the log in screen comes up but the keyboard and mouse do not respond. So I am stuck at the log in prompt unable to input the password to continue boot up.

PC only has input for USB keyboard + mouse, no PS/2 connectors.

Boot with recovery mode is possible, and after log in I have a CLI available with working keyboard. However, after inputing "StartX" command, the desktop shows up but the Keyboard + Mouse become inoperative.

Thanks in advance to all.

---

### Post by Perfect Storm on 2010-05-17
This is a known/common problem in 10.04

Which usb mouse/keyboard do you have?

---

### Post by Mountaineer on 2010-05-17
I enabled "legacy usb support" in the bios to enable the keyboard during boot.
Without it I couldn't select an OS to boot in grub.
I don't know if this is the same problem, but it can't hurt to try.

---

### Post by mayagrafix on 2010-05-17
> **Artificial Intelligence said:**
> This is a known/common problem in 10.04

Which usb mouse/keyboard do you have?

The mouse/keyboard are the stock items that came with the PC: Dell Inspiron 530. In short, the mouse/keyboard brand is Dell.

Well at least I now know my PC is not alone in bizzaro log in world.

---

### Post by mayagrafix on 2010-05-17
> **Mountaineer said:**
> I enabled "legacy usb support" in the bios to enable the keyboard during boot.
Without it I couldn't select an OS to boot in grub.
I don't know if this is the same problem, but it can't hurt to try.

Thanks for the tip. I'll give it a go shortly :KS

---

### Post by mayagrafix on 2010-05-17
> **Mountaineer said:**
> I enabled "legacy usb support" in the bios to enable the keyboard during boot.
Without it I couldn't select an OS to boot in grub.
I don't know if this is the same problem, but it can't hurt to try.

Went into bios to look for "legacy USB support" option but there is none offered. Thanks for the tip anyway. :KS

---

### Post by Mountaineer on 2010-05-17
A quick stroll around google shows that people have been having this problem intermittently since 2006!
The general consensus seems to be a bios issue leading to insufficient power being sent to the USB devices, but that smacks of voodoo to me, especially as many of the users state their boards work fine in live CDs or other OSs.
Sorry I can't be of more help and good luck.

---

