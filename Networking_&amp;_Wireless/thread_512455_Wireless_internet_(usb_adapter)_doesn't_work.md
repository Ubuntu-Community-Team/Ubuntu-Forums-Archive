---
title: "Wireless internet (usb adapter) doesn't work"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by billgoldberg on 2007-07-29
Yesterday I bought a new hp computer and installed ubuntu as my os (vista for other users).
I have been using ubuntu (7.04) for a while on my hp laptop and everything works.
On my new pc, the asus wlan adaptor driver is installed, the computer sees the networks and connects to my router, but i can't get on the internet. I checked and i didn't get an ip adress.

iwconfig:
lo        no wireless extensions. 

eth0      no wireless extensions. 

rausb1    RT2500USB WLAN  ESSID:"cpwbs15414D2A0"  Nickname:"" 
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=48 Mb/s   
          RTS thr:off   Fragment thr:off 
          Link Quality=55/100  Signal level:-59 dBm  Noise level:-201 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

fconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:19:21:D0:2F:4F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:21 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b) 

rausb1    Link encap:Ethernet  HWaddr 00:15:F2:7B:F5:7A  
          inet6 addr: fe80::215:f2ff:fe7b:f57a/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:1 dropped:0 overruns:0 frame:0 
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:561920 (548.7 KiB)  TX bytes:12742 (12.4 KiB) 

The philips router isn't a problem as my laptop can connect wirelessly and an another pc is connected by a cable. 

Any one knows a solution?

---

### Post by billgoldberg on 2007-07-29
Edit:
I got it working by deleting the network manager and installing wicd, it connected without problems.!!!!

This should be the standard instead of network manager.

---

