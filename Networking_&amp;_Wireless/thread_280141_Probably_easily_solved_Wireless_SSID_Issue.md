---
title: "Probably easily solved Wireless SSID Issue"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by Tennousei on 2006-10-19
My connection works just fine at home, Ubuntu recognized my wireless card and everything is AOK when it is allowed to find the SSID broadcast, however when I told it to look for linksys as the SSID (which it is) it would not connect. I didn't consider this a problem since I could connect without an SSID assigned in the Network Properties. Here's my problem...

At my school there is a wireless connection called URremote2day, they have MAC filtering and I am registered to connect (and can while running Windows XP) but when I assign the SSID in properties, or even in NetworkManager it can not connect. It may be a DHCP issue, but there is no network security and there should be nothing getting in my way. Please help.

---

### Post by Tennousei on 2006-10-19
I'm reading a signal strength but it maintains a "disconnected" status.

iwconfig

eth0   IEEE 802.11b  ESSID:"linksys"  Nickname:"HERMES I"
       Mode:Managed  Frequency:2.457 GHz  Access Point: 00:13:10:90:F0
       Bit Rate:2 Mb/s   Sensitivity:1/3
       Retry limit:4   RTS thr:off   Fragment thr:off
       Power Management:off
       Link Quality=46/92  Signal level=-51 dBm  Noise level=-96 dBm
       Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
       Tx excessive entries:0  Invalid misc:0  Missed beacon:0


ifconfig

eth0   Link encap:Ethernet  HWaddr 00:E0:63:50:9E:99
       UP BROADCAST MULTICAST  MTU:1500  Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
       Interrupt:3 Base address:0x100

PS. I have no ethernet capability on this laptop so I need to solve this issue with out connecting through ethernet.

---

