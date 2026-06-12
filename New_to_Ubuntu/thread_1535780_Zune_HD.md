---
title: "Zune HD"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by TimEnid on 2010-07-21
has anyone synced a zune with ubuntu without the use of wine or virtualbox? if so, how? I heard it can be done with Banshee, but im unable to detect it.

---

### Post by ubunterooster on 2010-07-21
Some say it can be synced with Amarok.

The only solutions I have found are with Amarok or VMware

---

### Post by AlphaLexman on 2010-07-21
Not to my knowledge, I have the original zune 30gb, ... my current linux kernel (2.6.31-32) will recognise the device and show the properties of zune's used and free disc space, but I cannot transfer or copy or view or play any files, mp3, jpg, etc from the zune device.

Proprietary software/hardware is against Linux! (imo)

---

### Post by Zeike on 2010-07-21
I have a Zune HD (wonderful device, *ducks*), and I use a Windows 7 installation in virtualbox with the standard Zune software.  It works swimmingly.  Just make sure you enable the Zune HD under usb devices in the virtualbox settings for your windows virtual machine.  I set my music directory up as a shared directory with my virtual machine (set to read-only, although that is optional).

As far as I'm aware there is currently no way to do it in wine or otherwise.

---

### Post by TimEnid on 2010-07-21
> **Zeike said:**
> I have a Zune HD (wonderful device, *ducks*), and I use a Windows 7 installation in virtualbox with the standard Zune software.  It works swimmingly.  Just make sure you enable the Zune HD under usb devices in the virtualbox settings for your windows virtual machine.  I set my music directory up as a shared directory with my virtual machine (set to read-only, although that is optional).

As far as I'm aware there is currently no way to do it in wine or otherwise.

i have done this also. while the zune shows up, my shared folders do not. i set my Music folder as shared in the settings and enabled usb support. i also set my external hd as shared also. when i start virtualbox, i see the driver for the external being installed, but it still doesnt show up

---

### Post by Zeike on 2010-07-21
> **TimEnid said:**
> i have done this also. while the zune shows up, my shared folders do not. i set my Music folder as shared in the settings and enabled usb support. i also set my external hd as shared also. when i start virtualbox, i see the driver for the external being installed, but it still doesnt show up

Wait, are you trying to set your external as shared, or as a usb?

If you set it as shared, virtualbox will set it up as a fake network drive, so you'll probably have to make sure network discovery is enabled in your virtual windows install to see those drives.

EDIT: Also, make sure you have installed the virtualbox guest additions.

---

### Post by TimEnid on 2010-07-22
> **Zeike said:**
> Wait, are you trying to set your external as shared, or as a usb?

If you set it as shared, virtualbox will set it up as a fake network drive, so you'll probably have to make sure network discovery is enabled in your virtual windows install to see those drives.

EDIT: Also, make sure you have installed the virtualbox guest additions.

my external is connected via usb. i have it set as a shared location. I will check to make sure network discover is enabled.

---

