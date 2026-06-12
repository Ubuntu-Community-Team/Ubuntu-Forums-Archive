---
title: "driver for modem"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by mustafa.alberta on 2011-01-04
hi friends,
i use D-Link DFM-562IS HSFi PCI Modem (COM3) on my PC and i want to use dell driver for this.
do you have any direct link?
i don't have access to the net through Ubuntu:confused: and i use Microsoft Windows XP):P.
kind regards,:KS

---

### Post by Bucky Ball on 2011-01-04
Perhaps should concentrate on why you don't have internet through Ubuntu. Is that modem connected to a router which you are trying to connect to via a cable or wirelessly? Give us some more specific description if you can. It will help us help you. :)

You really shouldn't need Linux drivers for a modem. Windows is connecting so I would say it is the way you have Ubuntu's network settings configured that is causing the problem.

---

### Post by QLee on 2011-01-04
[QUOTE=Bucky Ball]...
You really shouldn't need Linux drivers for a modem. Windows is connecting so I would say it is the way you have Ubuntu's network settings configured that is causing the problem.[/QUOTE]

Bucky Ball, that isn't a "real" modem, it is a software controlled modem which we often call "winmodems" because a windows driver is provided.


   	mustafa.alberta, you will need a Conexant driver for it. Here are a couple of links about Conexant modems. It isn't easy for a beginner and the Conexant drivers are not open source so there's no way to make it easy. Those were inexpensive modems meant to work with Windows drivers to save manufacturers money by not having to include hardware modems (which do their own processing and thus work directly from the serial port in Ubuntu).

Down about post 4 on this one.
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56)

[http://ubuntuforums.org/showthread.php?t=1621091&highlight=conexant](http://ubuntuforums.org/showthread.php?t=1621091&highlight=conexant)

---

### Post by Bucky Ball on 2011-01-04
> **QLee said:**
> Bucky Ball, that isn't a "real" modem, it is a software controlled modem which we often call "winmodems" because a windows driver is provided.


     

Cheers. ;)

---

### Post by cascade9 on 2011-01-04
> **QLee said:**
> Bucky Ball, that isn't a "real" modem, it is a software controlled modem which we often call "winmodems" because a windows driver is provided.

Yep. Right PITA they are as well. 3-4 years ago I tried with various different winmodems, and never had any joy with them. How much that was due to bad luck (both with hardware and drivers) or my lack of experience with linux distros at the time, I dont know. 

IIRC that modem uses the conexant chipset, and (insert random swearing here), the drivers are 'owned' by Linuxant. They used to make the proprietary drivers needed for that modem avaible for free, but they changed that years ago so you have to pay. 

You can still get a 'crippled' version for free, but that is limited tio 14 .4k. The full drivers are $20 US, and you can probably find a real hardware modem for that. 

Link to the linuxant site, just in case you want to see if those drivers work- 

[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

---

### Post by mustafa.alberta on 2011-01-05
hi friends,
i just asked for 'dell driver' for my modem.
thanks

---

