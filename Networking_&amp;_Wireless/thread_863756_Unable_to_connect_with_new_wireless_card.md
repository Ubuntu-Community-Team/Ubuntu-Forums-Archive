---
title: "Unable to connect with new wireless card"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by rasetsubo on 2008-07-18
I've been thru a wack of info here on the forum trying to solve my problem but I'm afraid nothing worked for me. So I kindly ask the masses to give me a hand. 

**/sbin/iwconfig**
lo        no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:"Rasetsubo69"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
[B]
/sbin/ifconfig[/B]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2588 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2588 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:129400 (126.3 KB)  TX bytes:129400 (126.3 KB) 


**lshw -C network**
WARNING: you should run this program as super-user. 
  *-network               
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: b 
       bus info: pci@0000:00:0b.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=32 module=ssb 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:22:15:12:eb:f5 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 

....so from the info above can someone tell me what the problem may be and how can I fix it so that I may access the internet.

Thanks

---

### Post by rasetsubo on 2008-07-18
/bump

---

### Post by rasetsubo on 2008-07-18
/bump

---

### Post by rasetsubo on 2008-07-19
/bump

---

### Post by rasetsubo on 2008-07-19
/bump

---

### Post by rasetsubo on 2008-07-19
please help

---

### Post by rasetsubo on 2008-07-19
/bump

---

### Post by rasetsubo on 2008-07-19
/bump

---

### Post by ugm6hr on 2008-07-19
Please stop bumping - every 12-24 hours is acceptable.

> product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 

This is your wifi.

What stuff have you tried already?

What version of Ubuntu?

Do you have wired access?

My advice - try searching for BCM4318 here or on google.  I believ the new b43 driver supports this - so it should work with the "Hardware Driver" enabled, provided you have wired access to enable it (and you haven't already tried editing device settings etc).

---

