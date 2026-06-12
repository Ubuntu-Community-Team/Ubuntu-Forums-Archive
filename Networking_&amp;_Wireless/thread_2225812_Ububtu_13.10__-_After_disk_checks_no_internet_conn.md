---
title: "Ububtu 13.10  - After disk checks no internet connectivity"
date: 2014-05-23
forum: Networking &amp; Wireless
---

### Post by hdeasy on 2014-05-23
Typing this on my windows laptop. After a disk check at start-up of my Ububtu 13.10 desktop PC this evening I found there was no internet connectivity anymore. Here some diagnostics. I had been logging in via my mobile - either USB connection or wireless. Now this is what I get:

sudo nm-tool
 
NetworkManager Tool
State: disconnected
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:0F:FE:C3:BA:A5
  Capabilities:
    Carrier Detect:  yes
  Wired Properties
    Carrier:         off

 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:fe:c3:ba:a5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f0500000-f0520000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14105 (14.1 KB)  TX bytes:14105 (14.1 KB)

I have no real idea what this means. Any suggestions as to how to return internet to the PC?

---

### Post by hdeasy on 2014-05-23
Solved!

I discovered it was the usb cable that was kaput.

---

