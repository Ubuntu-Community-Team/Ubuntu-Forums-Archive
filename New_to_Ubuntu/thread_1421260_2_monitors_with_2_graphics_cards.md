---
title: "2 monitors with 2 graphics cards"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by azzaw on 2010-03-04
Hi all.  I am new to Linux and Ubuntu.  I have a Nvidia 9800GT graphics card  running my main monitor.  I also have an ATI HD4670 card with HDMI out  hooked into my home theater amp for listening to music and watching  vids.  I have a dual boot system with Windows 7, and in Windows I can  run both cards at once allowing me to surf the net whilst listening to  music from my PC through the home theater system.  I am wondering how to  configure Ubuntu to run both of these cards at the same time.  If I  enable the ATI driver for in Admin/Hardware Drivers and reboot I loose my main  monitor and I have no signal to the home theater amp.  Has anyone had  this problem before and is it possible to run both crads at the same  time?
Also if the ATI driver has been enabled it boots into terminal.  If I type in startx I get an error.   Is there anyway of enabling the Nvidia driver without happening to reinstall thanks?

---

### Post by azzaw on 2010-03-07
O.K.  I hope this helps someone.   I found, after numerous re-installs, that I need to enable the Nvidia driver, under system/admin/hardware drivers.

Reboot.

Now enable the ATI graphics driver.

Reboot into BIOS and change the primary driver from PCI/PEG to PEG/PCI.  ( I have an Asus p5q motherboard and found this option under Advanced/Chipset/Northbridge/Initiate Graphics) 

Reboot.  Cool, I finally have Linux running through my TV.  Now I need to find out how to edit the xorg.conf file to suit.  

I was told about this:

[http://www.linux.com/archive/articles/113516](http://www.linux.com/archive/articles/113516)

from another thread that I had previously posted.  

After installing the Nvidia driver I took a copy of the Xorg.conf file. Then I took a copy of the Xorg.conf file with the ATI driver running.  I am not sure how to intergrate these file to make them act the same as the thread :[http://www.linux.com/archive/article]("http://www.linux.com/archive/articles/113516")[/113516  ]("http://www.linux.com/archive/articles/113516")
[B]
This is the xorg.conf file when the Nvidia driver is running:[/B]


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

**This is the xorg.conf file when the ATI card is running:**

  	 	 	 	 	 	  

 Section "Screen"
 	Identifier	"Default Screen"
 	DefaultDepth	24
 EndSection
 

 Section "Module"
 	Load	"glx"
 EndSection
 

 Section "Device"
 	Identifier	"Default Device"
 	Option	"NoLogo"	"True"
 	Driver	"fglrx"
 EndSection
  
Notice the only difference being the Driver.

Me, being fairly new to Linux, am wondering if any anyone know how to integrate these files to look like :[http://www.linux.com/archive/articles/113516](http://www.linux.com/archive/articles/113516)
Or does anyone know a better idea from here ?   
Thank in advance

---

