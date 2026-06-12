---
title: "Wireless internet works in windows, not in Ubuntu"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by joecreed on 2011-06-14
Hi everyone,

I am a complete newb when it comes to Ubuntu.  Just stumbled across it the other day when I was trying to figure out what to do with an old laptop.  I'm trying to find and operating system that is simpler, less maintenance, easier to use for my parents Dell Inspiron B130 computer.  Windows is getting really buggy and slow, but I installed Ubuntuu with Windows to try it out.

I think this is going to be good for them because all they really do is use the Internet.  I didn't want to get them a netbook, so I'm trying this.  Now to the point.  I installed Ubuntu and it seems to be working fine EXCEPT for the wireless internet.  No wireless networks are found so I can't connect to any.  Like I said, I'm totally new to this, so I have to ask for help.  Any insight would be greatly appreciated.  Thanks,

Nik

---

### Post by wildmanne39 on 2011-06-14
> **joecreed said:**
> Hi everyone,

I am a complete newb when it comes to Ubuntu.  Just stumbled across it the other day when I was trying to figure out what to do with an old laptop.  I'm trying to find and operating system that is simpler, less maintenance, easier to use for my parents Dell Inspiron B130 computer.  Windows is getting really buggy and slow, but I installed Ubuntuu with Windows to try it out.

I think this is going to be good for them because all they really do is use the Internet.  I didn't want to get them a netbook, so I'm trying this.  Now to the point.  I installed Ubuntu and it seems to be working fine EXCEPT for the wireless internet.  No wireless networks are found so I can't connect to any.  Like I said, I'm totally new to this, so I have to ask for help.  Any insight would be greatly appreciated.  Thanks,

Nik
Hi, put this command in a terminal 
```
lspci
```and post it back here by clicking on new reply and click # and paste the information between the brackets. You can open the terminal by ctrl+alt+t

---

### Post by joecreed on 2011-06-14
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Is that what you're looking for?

---

### Post by jony121 on 2011-06-14
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

### Post by Brushstroke on 2011-06-14
> 02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

There's your wireless. Now you might need to install a driver for it to get it to work.

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) 

I think this site should help you find the correct driver.

---

### Post by philinux on 2011-06-14
> **joecreed said:**
> Hi everyone,

I am a complete newb when it comes to Ubuntu.  Just stumbled across it the other day when I was trying to figure out what to do with an old laptop.  I'm trying to find and operating system that is simpler, less maintenance, easier to use for my parents Dell Inspiron B130 computer.  Windows is getting really buggy and slow, but I installed Ubuntuu with Windows to try it out.

I think this is going to be good for them because all they really do is use the Internet.  I didn't want to get them a netbook, so I'm trying this.  Now to the point.  I installed Ubuntu and it seems to be working fine EXCEPT for the wireless internet.  No wireless networks are found so I can't connect to any.  Like I said, I'm totally new to this, so I have to ask for help.  Any insight would be greatly appreciated.  Thanks,

Nik

Can you connect it wired directly to router. If so then do it and then look under system admin, additional drivers.

---

### Post by wildmanne39 on 2011-06-14
Hi, please do not use the link from jony121 it is very old you need to use an updated one, or try to get your driver from the additional drivers as stated in the previous post. Here is a link with the driver for your card the 4318. 
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44) you can also you the link by brushstroke.

---

