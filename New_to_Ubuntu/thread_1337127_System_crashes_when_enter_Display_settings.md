---
title: "System crashes when enter Display settings"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by snaudalius on 2009-11-25
System Settings -> Display
Then half of screen becomes black and the rest of it shows everything in very low resolution. Can restart laptop using logout dialog box but have to guess where to point mouse pointer and press because cannot see it. After restart everything is OK until I try to enter Display settings.

---

### Post by ukripper on 2009-11-25
what is your laptop's make and model number, and can you post output of the below command?
```
lspci
```

---

### Post by snaudalius on 2009-11-25
Sorry for not doing this in the first post. Dell Inspiron 6400.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by ukripper on 2009-11-25
Apparently, there had been a bug reported in past in relation to Dell laptops. Even my dell laptop vostro was effected with this bug. Probably you can try editing /etc/grub.d/40_custom by inserting the line **> i8042.reset i8042.reset i8042.nomux i8042.nopnp i8042.noloop** after each quiet splash in the file.



Then reboot and see if that works. We will go from there.


Here is bug report - [https://bugs.launchpad.net/ubuntu/+bug/334249](https://bugs.launchpad.net/ubuntu/+bug/334249)



.

---

### Post by snaudalius on 2009-11-25
nothing happened. I red about that bug and have to say that my keyboard and mouse remains active. It is just display problem. I get 640x480 resolution on the bottom of screen and black area on the top.

---

### Post by ukripper on 2009-11-25
ok can you go in system-->Administration-->Hardware drivers and see if your intel graphics driver is there.

and also go to System-->Preferences-->Display and see if you can change your resolution there.

---

### Post by snaudalius on 2009-11-26
Thank you for help. Now everything is working great. Strange but i did almost nothing. Noticed that from other user on the same system I get no errors when trying to set resolution but i my user problem remained. Then I tried to go to Applications->System->Screen resize & rotate. Got no dialog box or window but resolution became low. Managed to go to display settings and turn on high resolution. Now have no problems with display. 

P. S. Other problem occurred. I'm getting same 16 updates every day :) thinking about new OS

---

### Post by ukripper on 2009-11-26
> **snaudalius said:**
> Thank you for help. Now everything is working great. Strange but i did almost nothing. Noticed that from other user on the same system I get no errors when trying to set resolution but i my user problem remained. Then I tried to go to Applications->System->Screen resize & rotate. Got no dialog box or window but resolution became low. Managed to go to display settings and turn on high resolution. Now have no problems with display. 

P. S. Other problem occurred. I'm getting same 16 updates every day :) thinking about new OS

16 update everyday? Do you mean they are same updates you are receiving everyday or for different packages?

---

### Post by snaudalius on 2009-11-26
For those updates I am not sure but this week I had to restart my system few times and after each restart I get 16 packages and their names look quite same each time. restarts were done through shut down dialog. I will try to restart one more time and will see what will happen.

---

### Post by ukripper on 2009-11-26
can you update via terminal and if you see any error messages post here.

use below comand to update:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by snaudalius on 2009-11-26
after restart get 16 updates. here they are [http://img20.imageshack.us/img20/4939/printscreennr.jpg](http://img20.imageshack.us/img20/4939/printscreennr.jpg) 
will try your command after I get back from the cinema :)

---

### Post by snaudalius on 2009-11-26
It looks like the update problem is solved. I used to select all packages for update and press OK. Didn't noticed that something bad happens. Now pressed Apply and everything is good. I am a Linux user for almost a year but it is still some kind of magic for me :) Thanks for help :)

---

