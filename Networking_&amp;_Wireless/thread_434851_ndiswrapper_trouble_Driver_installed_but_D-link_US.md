---
title: "ndiswrapper trouble: Driver installed but D-link USB not available"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by TechnoMonkey76 on 2007-05-06
I need help!  I have a D-link DWL-G122 A2 USB wireless adapter.  It works in Windows, but not in Xubuntu!  I do not want to buy a new adapter, but when i installed the driver with ndiswrapper ([http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)) but even though it says "prisma02 : driver installed", it is still not recognizing the device!  ](*,) I can't get to the internet, and want to use Xubuntu all the time for it's speed and things.  I need my wireless to work!  Does anyone have a solution for me? :confused:

---

### Post by tomiu on 2007-05-06
what is output from:

ifconfig
iwconfig
lshw -C network

---

### Post by TechnoMonkey76 on 2007-05-06
Well, now i can't get xfburn to burn to a DVD-RW or erase it and Win Xp and Ubuntu are on different partitions.  Sorry, i am new to ubuntu.

---

### Post by TechnoMonkey76 on 2007-05-06
Sorry, i forgot i had CD-Rs.  :) 

ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by sruckh on 2007-05-12
I can not get the DWL-G122 V.A2 adapter to work at all in feisty.  BUG errors show up in /var/log/messages and dmesg when plugging in the adapter.  This is before trying to install any driver.  There is a crash in the USB kernel code.  

With just about every other linux distro, including 6.10 edgy, this adapter has worked fine with ndiswrapper if I use the drivers the came on the CD when I bought the adapter.  I had problems with the drivers that are currently available on the d-link web site.  They are for a different chipset and do not work.  Use the drivers that came with the adapter.

I still don't think it will work with 7.04.  I have tried upgrading from 6.10 to 7.04 and installing a fresh 7.04 system.  Either way, the DWL-G122 V.A2 adapter does not appear to work.

Scott

---

### Post by syphron12 on 2007-05-20
Exact same problem. Don't want to say new to Linux as it has been said countless times, but I am having serious trouble with this and don't know where to start.

---

### Post by littlefrog22 on 2007-08-23
I also have a DWL-122 D-Link USB dongle (REV. A2 as well)  and I can't make it work in UBUNTU 7.04 . Did you get any luck with yours since? Thanks, I am also an Ubuntu newB and will make the switch if I can make this work!

---

### Post by kevdog on 2007-08-24
Can you confirm that the chipset of the device is a prism chipset??  I think one strategy to install this device would be the winxp drivers with ndiswrapper, provided that the appropriate prism modules were blacklisted in the /etc/modprobe.d/blacklist file.  I believe you have to have done the following (I think):

blacklist prism54
blacklist islsm_pci
blacklist islusb
blacklist isl3886

and also have given this command:
sudo modprobe -r prism54

Again posting 
lshw -C network
lsusb -v
/etc/modprobe.d/blacklist

might help me get a better handle on your situation since Im kind of grasping at straws here!

---

### Post by Naike on 2007-08-24
I got a A-LINK usb adapter and ive installed ndiswrapper with the package program coming with ubuntu.
But no help either.

---

### Post by TechnoMonkey76 on 2007-12-16
I couldn´t get the internet for a while but now I have gotten 7.10 and it works.

---

### Post by MartinNemec on 2007-12-17
to littlefrog22:
this link may be helpful:
[https://help.ubuntu.com/community/WifiDocs/Device/DWL-122](https://help.ubuntu.com/community/WifiDocs/Device/DWL-122)

---

