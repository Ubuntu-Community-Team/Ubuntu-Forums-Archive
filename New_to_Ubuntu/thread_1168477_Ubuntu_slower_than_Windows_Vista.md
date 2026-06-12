---
title: "Ubuntu slower than Windows Vista?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by F1lo on 2009-05-24
Hello Ubuntu community,

I'm a new Ubuntu user, I installed it on my laptop a couple of days ago. I installed 9.04 Jaunty Jackalope. I thought Ubuntu was going to be faster than Vista, however, it is feels slower. Scrolling down pages in firefox, minimizing/ maximizing windows, watching videos, etc is slower than in Vista. I even checked System Monitor and it seems that it uses my processor much more than Vista. But I guess there must be something wrong because everybody keeps saying it is faster than Vista. My laptop has Intel Core 2 Duo processor T5250 (1.5 GHz, 2MB L2 Cache, 667MHz FSB), 2GB DDR2 System Memory, 120GB 5400RPM SATA Hard Drive, and Intel Graphics Media Accelerator X3100. I've read somewhere that I have to install the drivers for my videocard? I'm not sure, I'm really new to this. Any help with making my laptop run faster will be greatly appreciated.

---

### Post by sahabcse on 2009-05-24
open the terminal and type the following command on peak time and paste it


#top

#ps -ax

#free

---

### Post by Elfy on 2009-05-24
start with looking in hardware drivers in the system admin menu for a driver for your video.

---

### Post by gjoellee on 2009-05-24
I am just going to tell my opinion of this:
[B]
I have been using Ubuntu and XP on:[/B]
AMD Athelon XP 2.16 GHz
2 GB Ram
Nvidia GeForce Fx 5200

Ubuntu boots faster then XP, but the performance while running is about the same.

**My parants have Vista on:**
Intel Pentuim Dual Core 2.8 GHz
2 GB RAM
Nvidia GeForce 9800 GX2

Vista boots in about 30 seconds which is faster then XP on the other computer, but slower then Ubuntu's 21sec boot. Vista is also has a lot slower performance. I have doen a little test with Firefox:
In XP, Firefox opens in 5sec
In Ubuntu Firefox opens in 4 sec
In Vista Firefox opens in 8 sec!

---

### Post by davidsrsb on 2009-05-24
Take a look at System-Preferences-Appearance-Visual_Effects and try setting to None
Intel Graphics can be underpowered for too much Compiz windows animations

---

### Post by F1lo on 2009-05-24
System-Preferences-Appearance-Visual_Effects are already set to None. Also, when I look at System-Administration-Hardware Drivers it says No proprietary drivers are in use on this system.

---

### Post by growled on 2009-05-24
It's probably hardware related. No OS can work perfectly with every piece of hardware out there. Like others, I've done tests and Ubuntu is faster than Windows. 

Just do a search of the forum of your Intel X3100 and you'll more than likely find any answer you need.

---

### Post by shifty_powers on 2009-05-25
intel graphics are currently a major pain in the *** in ubuntu frankly...

---

