---
title: "noob Linksys Wireless WUSB54GC Adaptor"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by zoodsmak on 2008-12-24
Hello, I recently built a new box running stand alone Ubuntu 8.1. All hardware is up and running and I can connect to my wired internet and home network. This machine will be a DVR so I will need it to function wirelessly. I've picked up a Linksys WUSB54GC Adaptor and through the website listed I believe it should be compatible with Linux:
[http://linux-wless.passys.nl/query_part.php?brandname=Linksys]("http://linux-wless.passys.nl/query_part.php?brandname=Linksys")

more searching on [www.google.com/Linux](www.google.com/Linux) brings up lots of dialog about needing to istall Ndiswrapper but those threads all date back to 2005 or 2006 with previous versions of Ubuntu. I've tried Ndiswrapper and nothing seems to work. 

I will admit I'm a noobie and was introduced to linux last week after the install so I could easily be doing something wrong.

terminal information:
lsusb displays:
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 005 Device 002: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]**
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:21:97:8c:8f:8b  
          inet addr:10.0.1.200  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:97ff:fe8c:8f8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3336 errors:0 dropped:8274237942 overruns:0 frame:0
          TX packets:3315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3303862 (3.3 MB)  TX bytes:533990 (533.9 KB)
          Interrupt:254 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

I've run Ndiswrapper and installed the driver rt73 off the disk. Ndiswrapper installs the driver and claims to see the hardware.

has something changed in Ubuntu 8??? any info would be helpful.

Thanks

---

### Post by MrWES on 2008-12-24
Was there anything in System | Admin | Hardware drivers?

Also, that dongle should be supported in 8.10 kernel. Try this thread:

[http://ubuntuforums.org/showthread.php?t=946772]("http://ubuntuforums.org/showthread.php?t=946772")


Bill

---

### Post by mapes12 on 2008-12-24
Your device looks as though it is supported natively. You should not need ndiswrapper (which can be a bit hit and miss in any case). Try removing ndiswrapper rebooting and see if Ubu sets up wifi for you. You may have to do some tinkering around in Network Manager. I had a similar problem and out of frustration did a fresh install of Ubu where my card was configured correctly and good to go. If that doesn't work have a look at [WICD]("http://wicd.sourceforge.net/") which may get the device working.

---

### Post by zoodsmak on 2008-12-24
thanks for the link to the other thread. I'll admit I've spent alot of time searching the web for answers and totally forgot to search the archives of this forum.

I had a feeling it was supported when everything I found was dated back a few years. I've checked System>Admin>Hardware Drivers and all that appears is a Graphics Driver :(

I've removed the Ndiswrapper program and updated/ restarted a few times and all that shows up is my wired connection (I've even tried unhooking the cat5 line just to see if it would find the wireless device.)

since an lsusb command in the terminal shows the device hooked up why wouldn't it recognize the device???
I've checked the ect/modprobe.d/blacklist file and nothing seems to be relevant to this driver or hardware. 

I'll do some more archive searching but any other help would be appreciated!

---

