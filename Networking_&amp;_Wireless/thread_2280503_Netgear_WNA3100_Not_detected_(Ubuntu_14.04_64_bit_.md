---
title: "Netgear WNA3100 Not detected (Ubuntu 14.04 64 bit LTS)"
date: 2015-05-31
forum: Networking &amp; Wireless
---

### Post by miah2 on 2015-05-31
[Edit: Tldr: see first response by chili555 for solution]

Hi there,

I have recently Installed Ubuntu 14.04 64bit from a ROM file off an external HDD (partitioned alongside my Windows 7 OS) and have been unable to connect to my WiFi via my Wireless Network Adapter (Netgear N-300 WNA3100) as it does not seem to be connected/identified.

I have attempted the solution provided at: [http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251) which seems to have installed all the relevant files and drivers but even after restart and software updates the PC still does not identify any network adapter being connected.

Similarly I have attempted to install various Windows versions of the drivers for the adapter from the Netgear website (link: [http://downloadcenter.netgear.com/en/product/WNA3100#searchResults](http://downloadcenter.netgear.com/en/product/WNA3100#searchResults)) and install the drivers via Wine, however the installations either complete and again show no sign of any change, or they stall mid installation (repeats installation steps in a loop with no resolution or does not progress to the completed stage). 

As I am very new to ubuntu I am unsure which other details to provide, however in case it is useful please find the lsusb info from Terminal below:[INDENT]miah@miah-G5105uk:~$ lsusb
Bus 001 Device 007: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 008: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 001 Device 010: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 002: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 002 Device 002: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/INDENT]


Please also find details of the PC being used below:[INDENT]Device: HP G5105uk
Memory: 3.9 GiB
Processor: AMD Athlon(tm) II X4 640 Processor × 4
Graphics: Gallium 0.4 on NV98
OS Type: 64bit
Disk: 137.8 GB
[/INDENT]


Please feel free to ask for any tests or further information to assist with the problem I would be very glad to provide. 

Thank you very much in advance for any help!


-Miah

---

### Post by chili555 on 2015-05-31
Please see: [http://ubuntuforums.org/showthread.php?t=2264020](http://ubuntuforums.org/showthread.php?t=2264020)> I don't believe this device can be made to work correctly in Ubuntu 14.04 and later. Please don't ask me to help. I've tried everything I know of and it doesn't work.

---

### Post by miah2 on 2015-05-31
Thanks Chili555,

Somehow I didn't come across this thread in my days of searching (just goes to show the extra 2 hours of looking are always worth it). 

Thanks again for the help and prior efforts in trying to solve the issue!

---

