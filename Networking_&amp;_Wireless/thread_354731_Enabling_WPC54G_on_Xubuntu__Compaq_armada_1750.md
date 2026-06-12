---
title: "Enabling WPC54G on Xubuntu / Compaq armada 1750"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by user_of_gnomes on 2007-02-06
Hello,

I'm trying to get my Compaq Armada 1750 to work with my Wireless WPC54G (Linksys) PCMCIA card

I've followed the instructions at [u][url=https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]WifiDocs/WirelessTroubleShootingGuide
[/url][/u] and ended up at 

“4.2.5. Driver looks ok, device disabled: Go to the  ubuntu forums and ask, maybe someone else has the same laptop and knows the work around.”.


Subject: 

Xubuntu XFCE 4.3.99.1 
Compaq Armada 1750 
Linksys Wireless-G WPC54G Version 3

Output: 

laptop@laptop:~$: lshw
-network DISABLED
          description: Wireless interface
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@02:00.0
          logical name: eth0-network DISABLED
          description: Wireless interface
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@02:00.0
          logical name: eth0
          version: 02
          serial: 00:14:bf:b0:1a:a4
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic ip=192.168.1.10 link=no multicast=yes wireless=IEEE 802.11b/g
          resources: iomemory:12000000-12001fff irq:11
          version: 02
          serial: 00:14:bf:b0:1a:a4
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic ip=192.168.1.10 link=no multicast=yes wireless=IEEE 802.11b/g
          resources: iomemory:12000000-12001fff irq:11


laptop@laptop:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Comments:

WEP enabled, Linksys WRT54G EU router (V7.4). WPA2/AES works under Windows XP (And on the laptop under XP) 

Any suggestions are much obliged! I'm not very knowledgeable when it comes to Linux, actually, I had to look up a guide on how to mount a floppy drive so I could copy the output to my XP PC.. 
but I could continue learning if I got the wireless connection to work.

---

### Post by user_of_gnomes on 2007-02-08
Still haven't got a clue. Am I not providing sufficient information?

---

### Post by aeb1 on 2007-04-07
Wireless operation on the Armada 1750:

I bought the GIGAFAST USB Wireless card & plugged it in to the USB port. Instant connectivity! You still have to link to an SSID and set up communications to your wireless access point.  :biggrin:

---

