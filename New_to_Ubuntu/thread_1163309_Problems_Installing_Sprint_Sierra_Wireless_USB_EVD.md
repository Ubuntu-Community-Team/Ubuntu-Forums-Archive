---
title: "Problems Installing Sprint Sierra Wireless USB EVDO Modem"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Poppa0418 on 2009-05-18
Hello,

First off, I am VERY new to Linux/Ubuntu. I have been using it for about a week. (I am not even using it, this is a friend's laptop that I am attempting to help him with)

Ok so, I am using a Dell mini 9 netbook with Ubuntu 8.04 Hardy installed. Wired and Wireless networking both work fine. I am trying to install this USB Sprint aircard 589U by Sierra Wireless. 

I downloaded and went throught the guide that Sprint.com has provided. This guide suggests using KPPP which I cannot install on this laptop because it is not supported on my computer type (lpia). 

After some research, I found out I was able to use Gnome-PPP, after reading some posts, i got it to work! (At least i think i did) It dialed, and gave me a valid ip address. 

So i wanted to make sure it was working correctly and that the aircard was giving me internet access and not the wireless, so i disabled the wireless and restarted the laptop. Since I have done this, I have not been able to get the laptop to detect the aircard. Ive read a million posts and tried a thousand methods, none of which seem to work.

the output of my dmesg is as follows:

usb 2-1: new full speed USB device using uhci_hcd and address 3
usb 2-1: configuration #1 chosen from 1 choice
usb-storage: device ignored
sierra: probe of 2-1:1.0 failed with error -5
usb  2-1: USB disconnect, address 2
usb 2-1: new full speed USB device using uhci_hcd and address 3
usb 2-1: configuration #1 chosen from 1 choice
scsi5 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 5:0:0:0: Direct- Access      Sierra  Wireless Storage 2.31 PQ: 0 ANSI : 2
sd 5:0:0:0: [sdbd] Attached SCSI removable disk
sd 5:0:0:0: Attached scsi generic sg1 type 0


The result of lsusb is as follows:

root@sdot:~# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1199:0025 Sierra Wireless, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0c45:63e4 Microdia 

so it recognizes it, but when i open gnome-ppp and try to detect the modem on any and all devices i get no modem found on your system or cannot detect modem

I can see the modem attached in lsusb with the correct vendor and product IDs, but when i run dmesg, i get

sierra: probe of 4-2:1.0 failed with error -5

and it is not attached to any tty/USB* 

Please help, i need a professional, an expert!

Any help would be greatly appreciated. Thanks.

---

