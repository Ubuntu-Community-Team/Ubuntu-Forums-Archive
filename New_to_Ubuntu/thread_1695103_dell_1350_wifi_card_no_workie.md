---
title: "dell 1350 wifi card no workie"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by DGINSD on 2011-02-25
I'm a very new Ububtu user I have a dual booted machine with windows xp on thwe other half and Im so frustrated I'm about to throw my computer out the window
 
I cant get my wifi card working and Ive tried some of the tutorials for using ndiswrapper but no joy. apparently Im extra stupid and need very clear step by step help.
 
I have the [COLOR=green]ndiswrapper-1.56.tar.gz[/COLOR], [COLOR=green]ndiswrapper-common_1.54-2ubuntu1_all.deb[/COLOR], and [COLOR=green]ndisgtk_0.8.5_i386.deb [/COLOR][COLOR=black]in my home folder but when I try to use terminal to install them it says I dont have them please help i know its just a matter of getting past using the terminal rather than a interface[/COLOR]

---

### Post by migs73 on 2011-02-25
Have you tried to get a wired connection, then click on  System-->Administration-->Additional Drviers.

It'll then see if there are any available for your wireless card.

If not could you open a terminal (Ctrl+Alt+T or Applications-->Accesories-->Terminal) and type (or copy/paste from here);
```
lspci
```

And post the output back here. That will tell us what type of Wireless card you have.

Mike :)

---

### Post by DGINSD on 2011-02-25
The only internet connection I have is wireless ("borrowed" from a unsecured network) I can connect OK through the Windows XP partition and also from the family laptop. 

I'm not at home right now but as soon as I get off work I'll post the results of that command in terminal.

With my machine being dual boot and with everything on my windows partition working properly would I be safe to assume once I get ndiswrapper working i can simply use all those drivers? Also one instruction I saw said I needed to blacklist the wifi drivers that came with the Ubuntu install that aren't working, but the instructions didn't say how to do thet?

---

### Post by DGINSD on 2011-02-25
here is the results of the lspci command
 
[EMAIL="david@david-Inspiron-1150:~$"]david@david-Inspiron-1150:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
[EMAIL="david@david-Inspiron-1150:~$"]david@david-Inspiron-1150:~$[/EMAIL]

---

### Post by josephmills on 2011-02-25
ok so you need a b43 driver which is a proprietary driver for the BCM4306  (Rev. 3) that is why it is not working out of the box ¨once you get that driver you will be on-line via wireless. so you dont need any of the things mentioned above that you have  ndrapper ect. how to get the b43 driver with no eth0 is not that hard to do.  windoz supports the bcm4306 (rev 03) that is why you get wire-less on that part of your partition.Here isd a link to the fine folksa over at the linux wireless.  [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)     also do you have any usb sticks?

---

### Post by DGINSD on 2011-02-25
yep got a usb stick but it's very old and very small 256MB. 
 
So am I understanding correctly I will not need to use ndiswrapper? If not thats great but I still would like to find out why I couldn't get it installed and working, but thats a issue for another time. right now I just want my internet.

---

### Post by josephmills on 2011-02-25
> **DGINSD said:**
> yep got a usb stick but it's very old and very small 256MB. 
 
So am I understanding correctly I will not need to use ndiswrapper? If not thats great but I still would like to find out why I couldn't get it installed and working, but thats a issue for another time. right now I just want my internet.
 ok check out this link [http://ubuntuforums.org/archive/index.php/t-763995.html](http://ubuntuforums.org/archive/index.php/t-763995.html)

---

### Post by DGINSD on 2011-02-25
I'm up and running the link to linux wireless workd like a charm quite a bit of reading and work but at least I can get on line now. Thank you so very much. 
 
For what its worth that link should be put at the top for newbs with dells and wifi issues

---

### Post by josephmills on 2011-02-25
> **DGINSD said:**
> I'm up and running the link to linux wireless workd like a charm quite a bit of reading and work but at least I can get on line now. Thank you so very much. 
 
For what its worth that link should be put at the top for newbs with dells and wifi issues

good to hear have fun with it! once you get a chance You should mark the tread as solved. once again have fun with ubuntu.

---

### Post by DGINSD on 2011-02-25
Wait I lied, it will stay on for a bit but then go out, what gives?
 
Do I need to blacklist the drivers that came with the Ubuntu install, if so how does one do that

---

### Post by DGINSD on 2011-02-25
Just a thought I had both times it shut off I was updateing and it shut off mid-update is the system updateing to another driver that doesn't work?

---

### Post by DGINSD on 2011-02-26
It seems to be staying connected now that I got through the security updates I had to disable and re-enable the wireless connection by right clicking the internet icon at the top left till I got through the whole package hope that helps anyone else with a similar issue.

---

