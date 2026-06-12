---
title: "Setup Wireless?"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by JohnnyTricksta on 2007-11-03
Hi,

I just put a fresh install of Ubuntu 7.1 on my laptop since it finally supports my broadcom 4328 802.11a/b/g/n card. I'm looking at it and it shows it installed in the device manager. However, I can't figure out how to set it up?? I've looked everywhere I think I would find it. I thought it would be under System:Administration:Network but it only provides me options for a wired and modem connection. No wireless :confused:

Any ideas? (please keep in mind that I'm pretty new to Linux so answers that are step by step would be greatly appreciated)

Thanks!
Jordan

---

### Post by kevdog on 2007-11-03
Here is some background info, let me know if it helps you (if any):

[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

### Post by JohnnyTricksta on 2007-11-03
Hi Kevdog! Thanks for the prompt reply!

I installed Wicd and have that running. However, it says it can not find any wireless networks. I was browsing around the Ubuntu forums and saw to run this command to see if a driver is installed properly: lshw -C network

It came back with this:
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
 
Since it came back unclaimed, does that mean it is installed wrong??

Thanks again!

---

### Post by kevdog on 2007-11-03
> *-network UNCLAIMED
description: Network controller
product: BCM4328 802.11a/b/g/n

You have a broadcom card and need a wireless driver to use the card.  You will probably need to use ndiswrapper/winxp drivers to complete the installation.  I think in the bottom of the thread I posted above, there is a post by jamie jackson which explains how to do this.

---

### Post by JohnnyTricksta on 2007-11-03
> **kevdog said:**
> You have a broadcom card and need a wireless driver to use the card.  You will probably need to use ndiswrapper/winxp drivers to complete the installation.  I think in the bottom of the thread I posted above, there is a post by jamie jackson which explains how to do this.
I see it is made for Feisty. I have Gutsy, will it still work for me?

---

### Post by kevdog on 2007-11-03
The process is no different. I prefer to install from source, however do whatever method works for you.

---

### Post by JohnnyTricksta on 2007-11-03
Ok, it looks like it installed the driver. However, for some reason it still doesn't connect. It just sits there and tries to obtain a IP address then stops. Does it matter if I'm using WEP vs WPA?

---

### Post by kevdog on 2007-11-03
Dont use wpa for now, but wep is ok.  wpa requires more work, more packages to install.

iwlist scan

What does this show?? If nothing then post
lshw -C network

---

### Post by JohnnyTricksta on 2007-11-03
> **kevdog said:**
> iwlist scan

```
jordan@jordan-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:0E:78:E9:12
                    ESSID:"07B406055675"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
```

---

### Post by kevdog on 2007-11-03
Make sure you have a WEP key (not WPA).

Follow the link in my signature for connecting from the command line -- lets make sure everything works.

---

### Post by JohnnyTricksta on 2007-11-03
```
jordan@jordan-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1a:73:6b:de:bf
Sending on   LPF/wlan0/00:1a:73:6b:de:bf
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by JohnnyTricksta on 2007-11-03
Also, here is how I have Wicd setup:

---

### Post by kevdog on 2007-11-03
Can you try turning the WEP off??

---

### Post by JohnnyTricksta on 2007-11-03
I turned off WEP on my router, but for some reason it still hangs when trying to obtain an IP address

---

### Post by kevdog on 2007-11-03
What are the parameters you are passing on the command line?

---

### Post by JohnnyTricksta on 2007-11-03
Thanks so much for your help!!

```
jordan@jordan-laptop:~$ sudo ifconfig wlan0 down
[sudo] password for jordan:
jordan@jordan-laptop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 22703
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1a:73:6b:de:bf
Sending on   LPF/wlan0/00:1a:73:6b:de:bf
Sending on   Socket/fallback
jordan@jordan-laptop:~$ sudo ifconfig wlan0 up
jordan@jordan-laptop:~$ sudo iwconfig wlan0 essid "07B406055675"
jordan@jordan-laptop:~$ sudo iwconfig wlan0 key (my_key_here)
jordan@jordan-laptop:~$ sudo iwconfig wlan0 mode Managed
jordan@jordan-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1a:73:6b:de:bf
Sending on   LPF/wlan0/00:1a:73:6b:de:bf
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by JohnnyTricksta on 2007-11-04
Anybody? If I can't get this to work I sadly won't use Ubuntu. I need this working since I spend most of my time at the University and my house which are both wireless :(

---

### Post by kevdog on 2007-11-04
Try changing the essid on the router to begin with a letter and not a number.  Turn off WEP for no.  Lets break it down to basics.

---

### Post by JohnnyTricksta on 2007-11-04
I changed my essid and turned off encryption. When I do that I'm able to connect. Attached is a screenshot of my router's setting

---

### Post by JohnnyTricksta on 2007-11-04
SO I figured it out :) I had to use wext as the WPA supplicant driver and that took care of it.  Kudos and many thanks go to all your help. It was really appreciated!!!

---

