---
title: "Wireless Wont Work"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by rlondre on 2008-07-20
[B]Many hours now and still cant get my wireless to work. arrrrrr!!!

I checked the type of wirless card and installed the appropriate driver, I think.[/B]
*-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb

**I checked to be sure the device is on, it appears that it is.**
 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:6b:a2:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

**I checked to see if it is connected to the router and it appears that it  is not.**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**Next I simply decided to disable the wireless security on my router and still get no connection. What's going on? What can I do?**

---

### Post by rlondre on 2008-07-20
Just another comment on what else if tried and am now hung up on. 

I also decided to try using ndisgtk however the win driver for the wireless card in an .exe file and ndisgtk wants a .nif file. How does this work?

---

### Post by Rob-s on 2008-07-20
you can use 7zip or something else to open the exe file and maybe you can find the driver file there.

---

### Post by rlondre on 2008-07-20
Okay, now I've finally got it sort of working. However, every time I reboot  I have to go to network settings and change the password type back to WPA2 Personal and reenter my password. How can I stop this issue? I don't think I should have to go through this process every time I want to use my laptop. Besides my wife will never figure it out when she wants to use the laptop.

---

### Post by sputnikkk on 2008-07-20
Im in the same boat with just a different card. WAP2 setting and PWD lost upon reboot. It seems like the NetworkManager utility is borked in Hardy Heron 8.04.  Boggled.

Im saddled with RaLink drivers and apparently the workaround is to install .... drum roll please ... **Windows Drivers** [un-effing believeable ...  and use ndiswrapper. 

At this point - I could have bought 25 different wireless nics that "just work" for the value of my time spent futzing with this bug and the workarounds. 15hrs + - stubborn and stupid.

---

### Post by malfist on 2008-07-20
I beleive you can manually configure it in /etc/networks and disable NetworkManager

---

