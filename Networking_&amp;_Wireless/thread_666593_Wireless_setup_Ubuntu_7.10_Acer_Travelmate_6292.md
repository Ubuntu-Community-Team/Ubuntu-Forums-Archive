---
title: "Wireless setup Ubuntu 7.10 Acer Travelmate 6292"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by glenna on 2008-01-13
I started the troubleshooting process from this link:  [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Here is the info from my terminal:

-v3.23 ip=192.168.1.103 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:a9:5a:2b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
glenn@glenn-laptop:~$ sudo ifconfig wmaster0 down
[sudo] password for glenn:
glenn@glenn-laptop:~$ sudo dhclient -r wmaster0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
glenn@glenn-laptop:~$ sudo ifconfig wmaster0 up
SIOCSIFFLAGS: Operation not supported
glenn@glenn-laptop:~$ sudo iwconfig wmaster0 essid "Korn"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
glenn@glenn-laptop:~$ 

One last thing:  In my network tools, all I see is: wlan0 and wlan0:Avhi
Wired internet access works great.

Any hint about what I am doing wrong would be great!  
Thanks, 

Glenn

---

### Post by dromas on 2008-01-15
[http://ubuntuforums.org/showthread.php?t=497686&highlight=Santa+Rosa]("http://ubuntuforums.org/showthread.php?t=497686&highlight=Santa+Rosa")

I've got the 6292 too. For me the wireless card works fine with an adjustment:
ndiswrapper -ma instead of ndiswrapper -m

---

### Post by notanatheist on 2008-02-03
FWIW, I'll be buying the TM6292 this week. I've already done a test install of Ubuntu 7.10 (not a derivative like Kubuntu). Wireless and video were flawless. LED for bluetooth works but the LED for wireless didn't work. Make sure the wireless radio is on. 

Also, I setup the wireless the standard geek way, "iwconfig wlan0 essid yourESSIDhere", dhclient wlan0. Connected and did  updates without a hitch. 

Hope that helps. I'll know more when I have my hands on mine this week.

---

### Post by nuclearpidgeon on 2008-04-05
> **notanatheist said:**
> 
Also, I setup the wireless the standard geek way, "iwconfig wlan0 essid yourESSIDhere", dhclient wlan0. Connected and did  updates without a hitch. 


You could also use nm-applet and NetworkManager. I use them and they are great. It should come pre-installed in ubuntu - the little networking icon in the tray.

---

### Post by shuttleworthwannabe on 2008-07-19
In hardy 8.0.4.1, follow these instructions to get the LED light on: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090)

---

