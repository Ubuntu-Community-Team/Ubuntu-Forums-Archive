---
title: "No network connection"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by tashimee2 on 2013-11-09
I'm new to ubuntu. I changed my motherboard and processor, now I can't connect to the internet, and it doesn't recognize my scanner. It's like nothing I plug in works, including my external hard drives. What do I need to do to get things working again.  Can someone tell me where to get drivers and how to install them?  What is a .gz file and how do I use one? New motherboard is: Gigabyte H87-D3H. New processor is: i5-4430.

---

### Post by tashimee2 on 2013-11-09
Would reinstalling ubuntu help?

---

### Post by ian-weisser on 2013-11-09
What does work?
What do you see when you boot?
Do you reach GRUB?
Do you reach a text login prompt?
Do you reach a graphical login prompt?
Are you able to log in?
Are you able to open a terminal after logging in?

Is there some reason you thing reinstalling would help? Was something wrong with the first install?

---

### Post by tashimee2 on 2013-11-11
Ubuntu 12.04 works just fine, like it used to before I changed my motherboard. I was wrong about my external drives, they do work. I can't get it recognize the scanner I've used many times before the change. It won't connect to the internet, I think I need an Ethernet driver. It recognizes the ide hard disk, but it won't recognize the ide optical drive (yes I have adapters for ide), but I think this may be a problem with bios not ubuntu. The drive is not showing up in bios either. I have a tri boot system with Win XP, but it crashes every time I try to boot into windows, I'm getting a copy of Win 7, I hope by loading the drivers through windows it will solve the drivers problem. What about the scanner?

---

### Post by ian-weisser on 2013-11-11
What show up in /var/log/dmesg when you plug the scanner into your system?

---

### Post by tashimee2 on 2013-11-11
Nothing.

---

### Post by ian-weisser on 2013-11-11
If nothing shows in /var/log/dmesg when you connect/disconnect hardware, then you have a likely hardware issue (cable, connector, power, etc). That's where the kernel logs new connections, even unrecognized ones.

Try with a USB stick, for example. dmesg lights up, the kernel is so happy you plugged it in!

Try the scanner with a different usb cable. Try both cables in a different usb port. Try the scanner in Windows, and/or on a different system.
Try different usb devices known to work with that cable and port. See if you can narrow down the hardware issue.

---

### Post by tashimee2 on 2013-11-15
I got so disgusted with the hole process a couple days ago, I said too hell with it and plugged in my old motherboard (I thought it had died) and it works just fine. So I returned the new motherboard. Problem SOLVED. The next time a go to buy a new motherboard, I will think about what to get alot more. I'll come ask you guys. Motherboards are really resilient creatures, aren't they!

---

### Post by ian-weisser on 2013-11-15
Sure...except the new one that was broken.

---

