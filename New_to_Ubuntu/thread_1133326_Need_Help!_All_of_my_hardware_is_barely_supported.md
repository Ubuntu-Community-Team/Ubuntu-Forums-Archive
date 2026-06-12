---
title: "Need Help! All of my hardware is barely supported"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by ngrieb on 2009-04-22
I have a few major issues with hardware compatibility, and I am new to setting up a Linux OS and solving bugs (I have been using Linux systems at work for about 4 years, but everything of course there is locked by admin root so noone can play with settings). 

Computer Specs:
Ubuntu 8.10
AMD Athlon 3000+
NVidia MX4 (Integrated GPU, 128 (hopefully to be replaced tomorrow))
DLink DWL500 Rev. B 
Philips FlexCam 100
Canon iPixma 1500
Visioneer Onetouch 8600
240 GB HD Space (80 is still in NTFS format on slave drive)
1 GB RAM

My woes begin with possibly the graphics card or driver. Any time any sort of high graphics, 3-D, or even desktop effects are implemented my computer either hangs (in the case of screensavers) or logs itself out as in the case of desktop effects or getting the main menu for CS:S loaded in WINE (not all that graphically awesome yet). Do you need cedega cvs to play CS:S? I thought WINE would do it?

Even worse my scanner is not to my knowledge supported at all. 

My printer, although I have tried a million different methods (including installing deb drivers directly from the web or using alien to convert RPM drivers to deb) does not even respond to the print command. Just says "idle".

My wireless card seems to be very touchy, and used to cause a hang with blinking caps and scroll lock, but for some reason has not done so in a while??? Atheros chip is apparently is not very nice to play with. 

And finally my camera works with Cheese, but is not correctly configured for Skype (I can see a working picture, but the color is mostly green, and banded, like when your computer monitors pins are not all the way in). I think Skype just doesn't recognize it, and I have not installed any driver specifically made for the camera on my computer, because I can't locate any. 

Can anyone help with this long list of problems...I've spent days trying to find drivers and follow tutorials of all kinds with hardly any luck. Any help would be greatly appreciated. I don't really want to rewipe and install Windows...  :-(

---

### Post by spiderbatdad on 2009-04-22
for skype, you can probably edit the file /etc/modprobe.d/options adding something like:
```
options v4l2 gamma=50
options v4l2 GRed=290
options v4l2 GGreen=310
options v4l2 GBlue=315
```Also skype sometimes needs help to run webcams with releases since 7.10. This little guide might help.
[http://www.uluga.ubuntuforums.org/showthread.php?t=1026188](http://www.uluga.ubuntuforums.org/showthread.php?t=1026188)

Also mad-wifi might help with your atheros wireless.

---

### Post by wsonar on 2009-04-22
Did you enable the restricted nvidia driver?
You might have gotten a notification about this?

---

### Post by ngrieb on 2009-04-23
Ya, the driver is enabled. 
NVidia Driver Version: 96.43.09

---

### Post by ngrieb on 2009-04-26
Well, I installed an ATI Radeon X1650 Pro to replace the NVidia 6800XT which died on me, and hence the crappy NVidia MX4, and all of the problems seem to be smoothed out as far as graphics go. Counter Strike now runs, although it is a bit slow, and I can enable my desktop effects without a random logout.

---

### Post by desertdog on 2009-08-23
You might be able to get your scanner to work using the Viceo backend. 


See [http://viceo.orconhosting.net.nz/](http://viceo.orconhosting.net.nz/) and [http://www.g-loaded.eu/2008/01/24/viceo-backend-for-sane-with-libusb-support/](http://www.g-loaded.eu/2008/01/24/viceo-backend-for-sane-with-libusb-support/).

---

