---
title: "Cannot connect to wireless"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by djino on 2007-07-25
Newbie here,

I just installed ubuntu yesterday. I am able to get online through my ethernet wired connection, but not wireless. I click on an option I see to connect to a wireless network and it asks for the SSID/security/etc.. I enter that.. and it looks like its attempting to try to connect, but then it doesn't connect.

I'm starting to think if it even has a wireless driver installed. But I recall somewhere seeing something that showed eth0 and eth1 (which I assumed was my ethernet and wireless connections). Is there not some sort of program that scans and gives me a listing of wireless devices in my area (just as windows does)?

I am rather stuck, not sure what to do. I have a linksys router and even reset the settings to it, and tried to connect.. but it wont connect.. I have a dual boot with Vista...able to connect fine there.

Help needed! Thanks

Summary:
Dell Inspiron 2200 (Notebook)
Dual boot with Vista/Ubuntu
Able to connect with wired connection
No sure on the type of wireless card installed.. I think Dell Wireless 1350 (or 1450) WLAN card

djino
"who needs to connect his wireless...newbie"

---

### Post by djino on 2007-07-25
I guess I should add a bit more information:

When I run the command:  sudo lshw -C network        (I get the following).

*-network: 0 DISABLED
         description: Wireless interface
         product: BCM4318  [AirForce One 54g] 802.11g  Wireless LAN Controller
         vendor: Broadcom Corporation
         physical id: 3
         bus info: pci@02:03.0
         logical name: eth1
         version: 02
         serial: 00:14:a4:25:15:ld
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master ethernet physical wireless
         configuration: broadcast=yes  driver=bcm43xx  driverversion=2.6.20-16-generic latency=64  link=no  multicast=yes  wireless=IEEE 802.11b/g
         resources: iomemory:dfdfe000-dfdffffff  irq:19


When I type:  lspci -v     (I get the following)

02:03.0 Network controller: Broadcom Corporation BCM4318  [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)
           Subsystem: Dell Unknown device 0005
           Flags: bus master, fast devsel, latency 64, IRQ 19
           Memory at dfdfe000 (32-bit, non-prefetchable)  [size=8K]


when I type: sudo lspci -n     (I get the following)

.....
02:03.0  0280:14e4:4318 (rev 02)


When I type:  sudo iwconfig    (I get the following)


eth1       IEEE 802.11b/g ESSID:""  Nickname:"Broadcome 4318"
              Mode: Managed   Access Point: Invalid
              RTS thr:off           Fragment thr: off
              Encryption key: off
              Link Quality=0/100   Signal level=-256 dBm   Noise level=-256 dBm
              Rx invalid nwid:0    Rx invalid crypt:0    Rx invalid frag:0
             Tx excessive retries:0   Invalid misc:0    Missed beacon:0

---

### Post by fredj on 2007-07-26
If you look at the output from lshw, it says that your wireless chip is configured as eth1 but it also says that
its disabled. Have you somehow manged to turn off wireless from the keyboard.

---

