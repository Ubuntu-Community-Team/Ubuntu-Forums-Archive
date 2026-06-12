---
title: "USB Flash drives not appearing"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-18
USB FLash drives are not appearing (in Places>computer) under Computer when I plug them in.

I have tried 2 different ones in a couple of different ports.

They work OK in XP

Any help?

---

### Post by ikt on 2009-10-18
Do any errors appear in the system log when you plug them in?

System > Admin > Log file viewer

---

### Post by smileyguy on 2009-10-18
Thanks for the directions (I needed it!)

I looked at syslog (for today's date) Nothing appeared.

Added a cronjob to make sure it was logging stuff (it iwas).

Nothing happens to that syslog when i plug in a USB flash frive which is known to be working under Windows (just checked it). :(

---

### Post by anewguy on 2009-10-18
I suspect the default rules in udev - some USB devices get mounted as owned by root.

Try this in a terminal window:

lsusb  --> does your device show?

now:

sudo lsusb  --> does your device show now?

you might also want to try sudo nautilus and see if you can see them with the places browser.

Post back the results and we'll go from there.

Dave :)

---

### Post by smileyguy on 2009-10-18
When I enter **lsusb** in the terminal the device pops up in Nautilus as it should!

Unplug an try again and it doesn't appear until I enter same command in terminal.

At **sudo nautilus** - Nautilus pops up. USB Flash device doesn't appear but when I try to browse to "computer" Nautilus pop up window says "*Could not display 'computer'*. *Nautilus cannot handle 'computer' locations."* Nautilus works fine if I just browse through  [I]GUI > Places.

At **sudo lsusb** -  flash device works fine

NB - both **lsusb** commmands show results below at terminal:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:0217 Hewlett-Packard LaserJet 2200
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[/I]PS - Can I just pull out* the USB flash drive. I may have selected "unmount volume"* at one stage in the past in an attempt to "safely disconnect from USB device" - as per Windows XP - Do I still need to do that and could that have caused a problem?

---

### Post by philinux on 2009-10-18
You must always unmount. Are you using a usb hub. I have a machine that needs an lsusb to get them to show up.

---

### Post by Jason Cook on 2009-10-18
> **anewguy said:**
> you might also want to try sudo nautilus and see if you can see them with the places browser.
You should never use sudo for graphical programs. You need to use gksudo. [[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo]](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo])
> **smileyguy said:**
> PS - Can I just pull out* the USB flash drive. I may have selected "unmount volume"* at one stage in the past in an attempt to "safely disconnect from USB device" - as per Windows XP - Do I still need to do that and could that have caused a problem?
It is not likely for that cause it not to mount. You should select "unmount volume" when remove it just so the computer know that it is being removed.

---

### Post by anewguy on 2009-10-18
> **Jason Cook said:**
> You should never use sudo for graphical programs. You need to use gksudo. [[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo]](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo])

Oopppss - while it usually works fine for things like gedit, something like nautilus does need the gksudo - thanks for pointing that out to the OP!


Since just doing a lsusb makes them show in nautilus, I think we can rule out a udev rule problem.  By default, a lot of USB devices get mounted as owned by root via udev, and can cause problems with devices not being seen.  Usually this seems to be more with things along the lines of cameras, etc., but wanted to be sure with your devices.

Dave :)

---

### Post by smileyguy on 2009-10-18
> **philinux said:**
> You must always unmount. Are you using a usb hub. I have a machine that needs an lsusb to get them to show up.

No hub. Staright into one of the ports on back or front (same result) - It just stopped working. I am sure it worked OK in the past (only had this install for a couple of weeks).

---

### Post by smileyguy on 2009-10-22
So nobody able to help me as to why I can only get my USB flash drives to appear using lsusb in Terminal?

---

