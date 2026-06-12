---
title: "Dual Boot? (Apology in advance lol)"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by BT1 on 2009-12-12
Hey I know this has been asked maybe a dozen other times in this area but I have to ask again.

I'm going to install windows 7 and xubuntu 9.10 on my HP Pavilion HDX 9400 Laptop because my IDT sound card does not work through linux, I only get sound through the headphone jack which is annoying when I have friends or family wanting to watch an online video with me. So, I'm going to install windows 7 on a small partition to dualboot with Xubuntu, but I want Grub to be the default boot manager without the windows 7 boot manager showing up. What do you suggest? How should I go about installing the systems in order?

Thanks for the assist.

---

### Post by garyed on 2009-12-12
Install windows first to make things easy.

---

### Post by QIII on 2009-12-12
Install 7.  Use its native partitioning tools to reduce its footprint to leave you the room you want for Ubuntu.

Install Ubuntu on what is left.  GRUB2 should control the boot process.

As a bit of advice:  Use manual partitioning and be sure to create a /home partition.  It makes things much easier if you should have to reinstall or when you do a fresh install of a newer version.

---

### Post by Dennis N on 2009-12-12
You should install windows first. Otherwise, it will take extra steps to get things right. Ubuntu's installer will automatically detect the Windows installation, suggest partition sizes for the disk, install Ubuntu, and provide the dual boot capability. You may want to give a bit more space for the Windows partition than the installer suggests.

Edit: 

Xubuntu uses the same installer.

---

### Post by BT1 on 2009-12-12
Great, thanks for the advice!
 
I did some thinking while waiting and figured it would be best to install 7 first since I've read other boot menu horrors in this very same part of the forums. Which is why I cringed as I wrote yet *one more* "UBUNTU/WINDOWS DUAL BOOT HELP!" thread.
 
I really wish I could just install 7 on virtual box and be done with it, but I tried that and still no sound out of my PC speakers. ;( here's hoping the next release fixes IDT sound card issues.

---

### Post by abeisgreat on 2009-12-12
> **BT1 said:**
> Great, thanks for the advice!
 
I did some thinking while waiting and figured it would be best to install 7 first since I've read other boot menu horrors in this very same part of the forums. Which is why I cringed as I wrote yet *one more* "UBUNTU/WINDOWS DUAL BOOT HELP!" thread.
 
I really wish I could just install 7 on virtual box and be done with it, but I tried that and still no sound out of my PC speakers. ;( here's hoping the next release fixes IDT sound card issues.

Did you try installing the VBoxAdditions? That might help with the sound thing.

---

