---
title: "No scanner detected."
date: 2011-03-31
forum: New to Ubuntu
---

### Post by abnordude on 2011-03-31
I use a "HP J410 SERIES 1050 DESKJET". It has printing as well as scanning as well as photocopying. So far, when I was in windows I could use all that through the software provided in the CD.
But in ubuntu, I'm not able to use the CD.
Well, I can still take printouts from the default printer in ubuntu.
But I'm not able to scan anything. 
PLease help me.

---

### Post by jtarin on 2011-03-31
You need to outline the steps you have taken to attempt scanning. Then we will be able to help.
[Or you can just go here.]("https://help.ubuntu.com/community/ScanningHowTo")

---

### Post by jerome1232 on 2011-03-31
So I googled your device model and "linux scan", first thing I got was a driver from hp. Try installing hp's driver.

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

edit: Some of the wording of their walk-through is confusing. It seemed to indicate that your's isn't supported but I checked the supported list, and your combo scanner/printer is in fact supported. I would also install xsane on your computer and try that.

---

### Post by abnordude on 2011-03-31
I tried Xsane. This is the result.

Failed to open device 'hpaio:/usb/Deskjet_1050_j410_series?serial=Cn........':
Device busy.

---

### Post by jerome1232 on 2011-03-31
Have you tried walking through the link jtarin provided in post number 2?

---

### Post by abnordude on 2011-03-31
> **jerome1232 said:**
> Have you tried walking through the link jtarin provided in post number 2?

Yes. So far. I have reached no where.

---

### Post by jtarin on 2011-03-31
Did you get to this part in the documentation?
> What if it says "No devices available"?
Reasons why you might get this message:

There is a permissions problem. You can run the scanning software as root.
Your scanner is not supported in Ubuntu. The most common type of scanner not supported is old parallel port or Lexmark All-in-One printer/scanner/faxes
The driver for your scanner is not being autoloaded
You need to install the firmware file (probably a *.fw or *.usb) for your particular scanner. You simply need to copy the file into /usr/share/sane/ In my case I got the firmware file from the CD that came with the scanner (if the file is not there, try installing the cd with WINE- don't use the program but search for the needed file and copy it or do a quick internet search) and copied this file "ccd548.fw" into /usr/share/sane/gt68xx/
If your scanner is a Mustek 1200 UB Plus you will need this file sbfw.usb then rename it to "PS1fw.usb" then put the file in the directory "/usr/share/sane/gt68xx" (remember to give read permission to all users)
You have a parallel port scanner and you are not a member of the scanner group. The device /dev/parport0 (or whichever parallel port your scanner is connected to) by default is only readable and writable by user lp and group scanner. You can become member of group scanner via the User Privileges tab of the Account Properties dialog in the User Settings (Users and Groups) administration tool.


---

### Post by abnordude on 2011-03-31
> **jtarin said:**
> Did you get to this part in the documentation?

I'm a newbie. I didnt understand what they're trying to explain.
Could you please tell me what to do?

---

### Post by jerome1232 on 2011-03-31
xsane is recognizing his device, it's just saying it's busy now.

I would personally

A) Log out, then log back in to make sure any group changes from having installed sane are in effect. 

From what I have searched "Device is busy" can be a permissions related issue, so reboot or just log out then log back in and see if it works

if not then

B) Try running xsane as root (press alt+f2, gksu xsane, click run) 

If that does work we have to figure out what permissions exactly are wrong, if it doesn't 

C) Try Running hp-setup, just to make sure it's detected your printer/scanner, maybe it will at least key us in on something that's not right.
```
sudo hp-setup
```

D) Try finding the firmware on the devices driver cd, a .fw file on there and copy it to /usr/share/sane

---

### Post by abnordude on 2011-03-31
> **jerome1232 said:**
> xsane is recognizing his device, it's just saying it's busy now.

I would personally

A) Log out, then log back in to make sure any group changes from having installed sane are in effect. 

From what I have searched "Device is busy" can be a permissions related issue, so reboot or just log out then log back in and see if it works

if not then

B) Try running xsane as root (press alt+f2, gksu xsane, click run) 

If that does work we have to figure out what permissions exactly are wrong, if it doesn't 

C) Try Running hp-setup, just to make sure it's detected your printer/scanner, maybe it will at least key us in on something that's not right.
```
sudo hp-setup
```D) Try finding the firmware on the devices driver cd, a .fw file on there and copy it to /usr/share/sane

I tried A. Same result.
B gives the same result too.
C detects the printer in USB connection.
I didnt try D becoz i didnt understand it.
could you please explain it.

---

### Post by abnordude on 2011-04-29
I upgraded my ubuntu to the latest edition.
It detected my scanner.
Thanks everyone for your help guys.

---

