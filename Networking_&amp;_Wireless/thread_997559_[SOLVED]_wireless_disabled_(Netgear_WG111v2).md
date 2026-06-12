---
title: "[SOLVED] wireless disabled (Netgear WG111v2)"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by diagonallemma on 2008-11-29
Hi, I'm running a fresh install of Xubuntu 8.10 on a Fujitsu Lifebook with broken onboard wireless and a Netgear WG111.v2 USB stick. The stick is recognized, and iwlist scan lists my wireless network. However, nm-applet shows both the onboard wireless and the Netgear wireless as 'disabled', and the 'Enable Wireless' checkbox is grayed out. How can I enable the wireless? I've also tried wifi-radar, which looks like it connects, I even get an IP address, but the connection doesn't work (can't ping etc.). Any ideas would be appreciated..


```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ANU-Access"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 03
       serial: 00:0b:5d:82:aa:76
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5788-v3.01 ip=150.203.226.195 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:1f:c3:46
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:59:33:6b:82:9d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1f:33:85:4d:34
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

```

$ sudo wifi-radar
Error for wireless request "Set Nickname" (8B1C) :
    SET failed on device wlan0 ; Operation not supported.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:33:85:4d:34
Sending on   LPF/wlan0/00:1f:33:85:4d:34
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 42.120.68.10 from 42.0.0.1
DHCPREQUEST of 42.120.68.10 on wlan0 to 255.255.255.255 port 67
DHCPACK of 42.120.68.10 from 42.0.0.1
bound to 42.120.68.10 -- renewal in 42148 seconds.

```

---

### Post by S-Fraz on 2008-11-30
I have the same problem..

Anyone know why?

---

### Post by S-Fraz on 2008-12-01
Ok, I got it working!

The B43 driver thats pre installed is what was picking up on it. For some reason It was not working right with it.

So I decided to use ndiswrapper like I have tried many times without luck!
There was some info that other guides left out.

One, just install ndiswrapper from the pool/n folder of your installation disk. It's easy. First ndiswrapper-common, then ndiswrapper-utils, then ndiswrapper-Somin->It's the graphical interface.

Two, BEFORE you install ndiswrapper add b43 to the blacklist: [By Terminal, Dah!]

```

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist

```

Three, after installing ndiswrapper, install the inf driver though the GUI or Terminal. Your choice. I did the GUI.
Then restart your computer! When you boot back up your adapter should be noticed by your computer. Go to System->Administration->Net Work.

Enter your details, press ok and wait! It should work!

---

### Post by ivikas on 2008-12-01
May be this Link can help you

[http://ubuntuforums.org/showthread.php?t=867721](http://ubuntuforums.org/showthread.php?t=867721)

---

### Post by diagonallemma on 2008-12-01
Thanks S-Fraz, that worked! 

In my case, the Netgear was properly recognized all along, so all I had to do was blacklist the broken onboard system...

```

sudo echo -e "blacklist ipw2200" | sudo tee -a /etc/modprobe.de/blacklist

```

...and reboot.

---

