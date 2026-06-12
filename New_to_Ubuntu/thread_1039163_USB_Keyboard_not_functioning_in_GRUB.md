---
title: "USB Keyboard not functioning in GRUB"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by pigSTI04 on 2009-01-14
I just did a fresh install of Intrepid (8.10) 64bit. I'm not able to get my usb keyboard to work when the GRUB menu is loaded. The keyboard works fine in BIOS, as well as in Ubuntu, it is only in the Grub menu that it doesn't work. 

I've done some searching and found older posts regarding a bug but haven't been able to find any up to dat information regarding this issue. If anyone can help or point me in a direction it would be greatly appreciated. 

Currently I have a ps2 keyboard plugged in when I want to choose a different operating system.

---

### Post by colsandurz on 2009-01-18
Go into your BIOS and look for something like "Legacy USB Keyboard Support" and enable that.  I had a similar problem and that fixed it.  It seems like you need to enable something in the BIOS, but without knowing anything about your BIOS I can't say for sure.

---

### Post by pigSTI04 on 2009-01-19
> **colsandurz said:**
> Go into your BIOS and look for something like "Legacy USB Keyboard Support" and enable that.  I had a similar problem and that fixed it.  It seems like you need to enable something in the BIOS, but without knowing anything about your BIOS I can't say for sure.

I tried this and it didn't get me anywhere. It messed up, I found a usb to ps2 kb adatper in my spare parts bin and connected the usb kb through that and wouldn't you know, I can now navigate the grub menu. Strange.

---

