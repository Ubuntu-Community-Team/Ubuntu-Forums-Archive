---
title: "Vodafone/Huawei k3765 modem"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by Inisfad on 2010-12-14
Please, I hope someone here can help me.  I have been trawling through commands for this problem for 2 days.  I originally was on Ubuntu 10.04 and tried to install a Huawei k3765 modem.  I am a real newbie, and frankly, after hours of inputting commands, my laptop no longer restarted or shut down.  I didn't know how to fix the problem, so I downgraded back to 9.10.  I have 2 Huawei modems.  One is the older e220 modem, and the other is a new k3765 modem.  My old modem installs perfectly, just plug n play.  However, Ubuntu sees the new modem as a mass storage/cd drive.  I cannot figure out how to change this setting.  I run lsusb and the modem is seen as Device 6; ID 12d1:1520.  Dmesg | grep shows the device as a CD-rom drive.  Frankly, I don't know a lot of commands, and am swarmed with all sorts of differing commands off the internet.  Does anyone know how to get the computer to see the 'cd' device as a modem, and how to install it?  Thanks

---

### Post by alexfish on 2010-12-14
Hi

try latest usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

follow link to debian site

alexfish

---

