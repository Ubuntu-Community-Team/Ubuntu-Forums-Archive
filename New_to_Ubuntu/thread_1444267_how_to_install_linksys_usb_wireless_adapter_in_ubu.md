---
title: "how to install linksys usb wireless adapter in ubuntu"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by yacin on 2010-04-01
[SIZE=4]Hello everyone, first time ever im using ubuntu. i just installed as dual boot with windows xp. im so confused how to make my linksys usb wireless adapter works with ubuntu. I apologize for my igonrance is the first time ever i use ubuntu. i dont know hoe to use command line and how to use linksys drivers from xp to ubuntu. If somebody have time to help me i will need step by step commands to accomplish the installation of the wirless drivers. Thank you very much.[/SIZE]

---

### Post by anewguy on 2010-04-01
The first step is for us to have more detailed information about the chipset on the adapter.  Please do the following and post the output back here:

in a terminal window (applications/accessories/terminal):

(with the device plugged into a USB port)

lsusb <press enter>


Post the output of that back here and we can try to go from there.

Dave ;)

---

### Post by Transbibilfobil on 2010-04-05
Hey srry, I'm not the OP, but i have the same exact problem, here are my results

arkt1k@Nullm00n:~$ lsusb
Bus 001 Device 008: ID 1737:0079 Linksys 
Bus 001 Device 002: ID 1058:1102 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 004: ID 1241:1503 Belkin Keyboard
Bus 002 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

so obviously, my bus 001 device 008 is the usb adapter. The model number on the back says WUSB600N ver.2

Any help would be appreciated!

---

### Post by yacin on 2010-04-05
Thank you very much for the feedback

---

