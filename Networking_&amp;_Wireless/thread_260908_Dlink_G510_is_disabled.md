---
title: "Dlink G510 is disabled"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by lars49 on 2006-09-19
I have a Dlink DWL G510 card. I have XP and ubuntu installed.
When I boot XP the card is working fine.
The command lshw says the device is disabled 

How do I enable it in UBUNTU 

/Lars

---

### Post by lars49 on 2006-09-19
The full name of card:
D-link Airplus G DWL-G510 Wireless PCI rev .C
I think the rev. C my cause the problem

I got the following from various commands

lshw   output
--------------------------------
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT61 Wireless


iwconfig output
------------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


lspci -v output
------------------------------

0000:01:0b.0 Network controller: RaLink: Unknown device 0302
        Subsystem: D-Link System Inc: Unknown device 3c09
        Flags: bus master, slow devsel, latency 64, IRQ 66
        Memory at dbef8000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [40] Power Management version 2

---

