---
title: "Madwifi on Hardy"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by nikRbokR on 2008-11-09
Could someone please guide me in installing the madwifi driver for the Netgear WPN511 wireless card?  I cannot seem to make sense of the online instructions on their site.

I really need to get this working soon... thanks!

---

### Post by kevdog on 2008-11-09
Madwifi drivers are included by default in the default install.  You only need to compile if you need to patch the sources

---

### Post by nikRbokR on 2008-11-09
So should I just be able to plug it in and run?

Edit: So I've done "make uninstall" in the madwifi-0.9.4 folder so that i undid the source that i had compiled.  Then I reinstalled the restricted drivers in Synaptic just to make sure.

---

### Post by nikRbokR on 2008-11-09
> **kevdog said:**
> Madwifi drivers are included by default in the default install.  You only need to compile if you need to patch the sources

You say the drivers are included by default.  Does that mean that I don't need to do ANYTHING?  Just put in my WPN511 card and run?  Or do I still need to do something?

I have used ndiswrapper to setup a wireless usb adapter (Netgear's WPN111).  Do I need to get rid of that driver?  When I do iwconfig, I don't get any "ath0" devices.

This is the output for iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Home2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:33:23:BC   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Have no idea what this means though.

I did restart, but the lights on the WPN511 card don't light up - so I'm not sure whats wrong...  I had to pull it out and put it back in to get the lights to show again.

BTW, this is my output for lshw -C network:
```
 *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:55:d4:5d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=24 mingnt=10
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:6c:e4:a8:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.52+NETGEAR,09/26/2005,1.5.0.21 ip=192.168.1.114 link=yes multicast=yes wireless=IEEE 802.11g

```

---

