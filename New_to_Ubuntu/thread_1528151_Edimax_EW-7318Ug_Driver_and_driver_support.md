---
title: "Edimax EW-7318Ug Driver and driver support"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by dcforeman on 2010-07-10
Hi, I love Ubuntu, it's fast, and compiz makes it a pleasing visual experience. (I am using the latest 10.04 LTS)

However, the driver support in it is absolute pants. I've fought to get wireless drivers install to install on OpenSUSE for my Dell Inspiron 1520. Ubuntu provided the solution in a nice neat graphical interface explaining exactly what I had to do. Fantastic.

This is not the case on my desktop, I've been using the Edimax EW-7318Ug happily on Windows 2000 to Windows 7. All I had to do was install a single EXE file and all's done.

But not with ubuntu, I've downloaded the linux drivers from the Edimax website, I've read the readme file, followed it through as best as my linux knowledge allows. All I'm getting is driver build errors, which you have to be a trained sodding programmer to understand. My experience with C is limited at best. I can't imagine most users have any knowledge of it at all. Asking such users to compile their own drivers is a blasted joke, and a cruel one at that.

So I searched for better instructions, and found [http://ubuntuforums.org/showthread.php?t=279946](http://ubuntuforums.org/showthread.php?t=279946) which must be badly out of date as even the wget line had me searching for an alternative location. I attempted to follow the same instructions for an updated driver file with no joy at all.

So if anyone has a nice simple installation method to get a this commonly used dongle working please let me know. I've spent a day reading the internet without anything remotely intelligible. Sensible or user friendly.

At this rate I'm going to throw off Ubuntu and Linux completely, and return to Windows. It might be slow, it might be bloated. But by god they know how to make the installation of sodding device drivers easy.

---

### Post by redbook4574 on 2010-07-10
> **dcforeman said:**
> Hi, I love Ubuntu, it's fast, and compiz makes it a pleasing visual experience. (I am using the latest 10.04 LTS)

However, the driver support in it is absolute pants. I've fought to get wireless drivers install to install on OpenSUSE for my Dell Inspiron 1520. Ubuntu provided the solution in a nice neat graphical interface explaining exactly what I had to do. Fantastic.

This is not the case on my desktop, I've been using the Edimax EW-7318Ug happily on Windows 2000 to Windows 7. All I had to do was install a single EXE file and all's done.

But not with ubuntu, I've downloaded the linux drivers from the Edimax website, I've read the readme file, followed it through as best as my linux knowledge allows. All I'm getting is driver build errors, which you have to be a trained sodding programmer to understand. My experience with C is limited at best. I can't imagine most users have any knowledge of it at all. Asking such users to compile their own drivers is a blasted joke, and a cruel one at that.

So I searched for better instructions, and found [http://ubuntuforums.org/showthread.php?t=279946](http://ubuntuforums.org/showthread.php?t=279946) which must be badly out of date as even the wget line had me searching for an alternative location. I attempted to follow the same instructions for an updated driver file with no joy at all.

So if anyone has a nice simple installation method to get a this commonly used dongle working please let me know. I've spent a day reading the internet without anything remotely intelligible. Sensible or user friendly.

At this rate I'm going to throw off Ubuntu and Linux completely, and return to Windows. It might be slow, it might be bloated. But by god they know how to make the installation of sodding device drivers easy.

What drivers are trying to install?? The edimax is supported out of the box by ubuntu with the rt61 drivers .

---

### Post by redbook4574 on 2010-07-10
sorry that should be the rt73usb driver, just plugged one into my ubuntu machine and it worked first time.

---

### Post by dcforeman on 2010-07-13
It should be yes. And this driver appears to be working and connected. It says it has a connection but whenever I load up Firefox it throws up the usual cannot connect page.

---

