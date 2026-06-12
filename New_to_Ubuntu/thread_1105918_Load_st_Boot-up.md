---
title: "Load st Boot-up"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-25
Ubunteros,

I believe my webcam loads at boot-up. How can I determine if this is the case?

Thanks!

---

### Post by balaknair on 2009-03-25
Try installing Camera Monitor(Applications menu> Add/Remove--> install Camera Monitor), it shows an icon in the system tray when your webcam is on.

Other options- Cheese, Camorama

---

### Post by suomalainen on 2009-03-25
First I'd like to determine if it loads at boot-up. I believe this to be the case as the little green light is on all the time.

---

### Post by balaknair on 2009-03-25
The green light might not mean that it's on and capturing video, just that the device has been detected and the module loaded in the kernel- ready to use. When the device is running(in use) the light will usually switch off or blink. 

Camera monitor shows an icon in the system tray when the camera is in use(ie, it is active).

---

### Post by suomalainen on 2009-03-25
No that's not it. Some time ago I opened up a setting to load this device at start up and now I want to go back to this file and look at it. I just forgot how to do it.

---

### Post by balaknair on 2009-03-25
You'll find that in the ***/etc/modules *** file, if you know what module your webcam uses.
If it loads at startup, it'll be listed there. What make is your cam?

---

### Post by suomalainen on 2009-03-25
logitech  F.Y.I..  /etc/modules does not exist. etc does but folder modules does not.

---

### Post by balaknair on 2009-03-25
/etc/modules is a file(the 'modules' file located in the folder '/etc')

Open it with Alt-F2--> *gksudo gedit /etc/modules*

Logitech cams I think will use the gspca driver, so there should be an entry gspca in the /etc/modules if it is set to load at boot up.

**_EDIT_**
Different models of Logitech cams use different drivers(not just gspca)
For a list of drivers used by various Logitech webcams see here:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

You should be able to see one of the listed drivers in your /etc/modules list.

---

