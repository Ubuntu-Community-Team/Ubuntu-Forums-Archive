---
title: "Ubuntu won't load from Disc"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by flee0308 on 2011-03-16
I am installing Ubuntu on a old notebook. I insert the disc and start up the computer. the notebook loads into the disc, but stops at the point where I can only see my mouse and the wallpaper of Ubuntu. Mouse works. 

Here's an image of the issue.

[http://i74.photobucket.com/albums/i259/flee0308/IMG_20110316_141832.jpg](http://i74.photobucket.com/albums/i259/flee0308/IMG_20110316_141832.jpg)

---

### Post by migrate from windows on 2011-03-16
Which version you are trying to install. Sometimes if your RAM is less this happens. Pls post details about your hardware.

---

### Post by flee0308 on 2011-03-16
10.10.

My cousin turned off the power by accident while I was reformating the computer. I don't have the windows disc with me, and I don't plan on using Vista on such a sluggish piece of hardware anyway. Here are the specs.

Operating System - Microsoft Windows Vista® Home Premium / Windows 7 (TBA)
Display - 33.7 cm/13.3 inch LED Backlit LCD HD (1366×768)
CPU - Intel Core 2 Dual T6500
CPU Speed - 2.1 GHz
FSB - 800 MHz
L2 Cache - 2 MB Cache
Memory - 2GB DDR2 800 (2,048MBx1)
Graphics - NVIDIA® GeForce&#8482; 8200M G
Stereo Speakers - (1.5W/ch), SRS WOW HD, SRS TruSurround HD
Hard disk - 320 GB
DVD Writer Super Multi (Dual-Layer)
Power Adapter - 65 W
Battery - 6 Cell
Dimensions - (WxHxD) 320 x 227 x 34~37 mm
Weight - 1.94 kg

---

### Post by migrate from windows on 2011-03-16
Your hardware is not sluggish by any way, Ubuntu runs well in much older laptops. While booting with the cd do you get a screen first where there is a logo of a man and a keyboard at the bottom middle?

---

### Post by NightwishFan on 2011-03-16
Try this, press a key when you get to the screen he mentioned above, with a white logo at the bottom, press any key. When you get to the menu, highlight install ubuntu (unless you want to try it first either way), press f6 and select "nomodeset" then press esc. Then push enter. Does it load a desktop or any programs. Also it might be wise to check the disk for errors.

If this works, then in your new install you might have to add nomodeset to the boot options, which is simple, but we can get to that when we come to it.

---

### Post by flee0308 on 2011-03-16
> **NightwishFan said:**
> Try this, press a key when you get to the screen he mentioned above, with a white logo at the bottom, press any key. When you get to the menu, highlight install ubuntu (unless you want to try it first either way), press f6 and select "nomodeset" then press esc. Then push enter. Does it load a desktop or any programs. Also it might be wise to check the disk for errors.

If this works, then in your new install you might have to add nomodeset to the boot options, which is simple, but we can get to that when we come to it.

Thanks, I finally installed Ubuntu. So what's nomodeset and how do I install it?

EDIT: I spoke too soon. I think I have an error. I seem to be stuck at a screen with the word "ubuntu" and 5 orange dots below it, which comes just after the ubuntu sound.

---

### Post by NightwishFan on 2011-03-16
You have to add nomodeset to your boot options likely. Hold shift while booting to get to recovery mode. When in recovery mode, choose "Root Shell" from the menu. Type the following command:
```
nano /etc/default/grub
```
This is a text editor. Do not edit anything except the like that looks like:
```
GRUB_CMDLINE_LINUX=""
```
Change it to:
```
GRUB_CMDLINE_LINUX="nomodeset"
```
Press CTRL+X and hit y to save the file, and then run:
```
sudo update-grub
```
When this finishes, press ctrl+alt+del to reboot.

Ubuntu should work.

---

### Post by flee0308 on 2011-03-16
Thanks, this worked well.

---

### Post by NightwishFan on 2011-03-16
Good I am glad! :)

---

### Post by flee0308 on 2011-03-17
> **NightwishFan said:**
> Good I am glad! :)

Okay, I realised there is one problem today. I don't have a GRUB menu (the one which gives me the choice to enter into normal ubuntu or recovery, etc). Would this become a problem in the future with grub updates like wubi?

---

### Post by NightwishFan on 2011-03-17
I think the grub menu is hidden by default unless you hold shift at the right time.

---

### Post by flee0308 on 2011-03-17
That's fine then, thanks.

---

