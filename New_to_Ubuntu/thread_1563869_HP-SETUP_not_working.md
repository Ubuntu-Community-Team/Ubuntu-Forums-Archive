---
title: "HP-SETUP not working"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by ianstump on 2010-08-29
Hello.

I have a problem :( When I try to run hp-setup in order to install the driver of my printer, it gives me an error of "no connection found" any ideas of how to resove this?

Thanks, Ian

---

### Post by ssdt on 2010-08-29
Weird but I get this error when I type that in the terminal:
[COLOR="DarkOrange"]
HP Linux Imaging and Printing System (ver. 3.10.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

/home/datta/.themes/Win7.Basic.02/gtk-2.0/panel.rc:7: Unable to locate image file in pixmap_path: "Panel/panel-bg.png"
/home/datta/.themes/Win7.Basic.02/gtk-2.0/panel.rc:61: Unable to locate image file in pixmap_path: "Panel/panelbutton.png"
/home/datta/.themes/Win7.Basic.02/gtk-2.0/panel.rc:64: Background image options specified without filename
/home/datta/.themes/Win7.Basic.02/gtk-2.0/gtkrc:77: Unable to locate image file in pixmap_path: "Handles/handle-v.png"
/home/datta/.themes/Win7.Basic.02/gtk-2.0/gtkrc:80: Overlay image options specified without filename
/home/datta/.themes/Win7.Basic.02/gtk-2.0/gtkrc:85: Unable to locate image file in pixmap_path: "Handles/handle-h.png"
/home/datta/.themes/Win7.Basic.02/gtk-2.0/gtkrc:88: Overlay image options specified without filename
/home/datta/.themes/Win7.Basic.02/gtk-2.0/gtkrc:1690: Unable to locate image file in pixmap_path: "Handles/handle-v.png"
/home/datta/.themes/Win7.Basic.02/gtk-2.0/gtkrc:1693: Overlay image options specified without filename
/home/datta/.themes/Win7.Basic.02/gtk-2.0/gtkrc:1697: Unable to locate image file in pixmap_path: "Handles/handle-h.png"
/home/datta/.themes/Win7.Basic.02/gtk-2.0/gtkrc:1700: Overlay image options specified without filename
Segmentation fault[/COLOR]
What printer are you using? Officejet?

---

### Post by sgosnell on 2010-08-29
Is the printer connected and turned on?

---

### Post by ssdt on 2010-08-30
Yes it is turned on for my case.

---

### Post by jpm_newbie on 2010-08-30
I used [this page]("http://hplipopensource.com/hplip-web/downloads.html") from the HP site and found I don't need to install anything.  However, the wireless part was set up using a Windows pc.

---

### Post by gordintoronto on 2010-08-30
> **ianstump said:**
> Hello.

I have a problem :( When I try to run hp-setup in order to install the driver of my printer, it gives me an error of "no connection found" any ideas of how to resove this?

Thanks, Ian

What printer?

---

### Post by sgosnell on 2010-08-30
Yes, what printer, and how is it connected?  USB?  Network?  Far too little information to make any informed recommendations.

---

### Post by ianstump on 2010-08-31
yes, sorry.
Its a 1020 Laserjet. It is connected via USB. Of course it is turned on.
When the hp-setup tries to download/install the driver, the "connection problem" appears. 

Thanks!

---

### Post by sgosnell on 2010-08-31
The first thing I would check is the USB cable and the USB port on the computer, and on the printer.  They can all be bad, and it's quick and easy to check them, although not quite as easy on the printer.

---

### Post by ianstump on 2010-08-31
Actually it is detected perfectly when plugged. Is there an alternative method to install the driver?

Thanks

---

### Post by sgosnell on 2010-08-31
Installing hplip should take care of it.  Hplip should recognize the model and get the driver for you, as should the printer wizard.  You should be able to just go to System/Administration/Printing, click on the New button, and have it find the printer and install the correct driver.  You don't need to do it manually.

---

### Post by ianstump on 2010-09-01
Isn't HPLIP and HP-SETUP the same thing?

---

### Post by sgosnell on 2010-09-02
No, they're different.

---

### Post by ianstump on 2010-09-20
Well, I still have the same problem, which is that I have the connection problem. Can I just download the specific driver, instead of the automatic search?

---

### Post by sgosnell on 2010-09-20
You can, but I doubt it will help.

---

### Post by GregA on 2010-09-21
The connection problem . . . . are you able to access the HP site now?   Perhaps the server or router was down when HP-Setup tried to download the the required "driver plug-in"

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html)

---

