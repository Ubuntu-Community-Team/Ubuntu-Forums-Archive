---
title: "Slow wifi speeds on ALFA AWUS036AXM USB Adapter (mt7921aun) despite high link quality"
date: 2024-03-24
forum: Networking &amp; Wireless
---

### Post by wascally314 on 2024-03-24
Hello,

My real world wifi download speeds are approximately 155 Mbit/s as measured on speedtest-cli. On my other wifi devices (windows machine and iPhone), I get speeds of 700 Mbit/s. These devices are all right next to each other about 20 feet away from the router.

I am running:
Ubuntu 23.10
Linux 6.8.0-060800rc7-generic #202403032133
ALFA AWUS036AXM USB Adapter (mt7921aun) 

iwconfig shows:
```
wlx<IF from MAC [IF3]>  IEEE 802.11  ESSID:"Verizon_Z3X4LW"  
          Mode:Managed  Frequency:5.56 GHz  Access Point: <MAC 'Verizon_Z3X4LW' [AC7]>   
          Bit Rate=1.2009 Gb/s   Tx-Power=3 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0
```

I have disabled IPv6. On the router, I have assigned a static IP address.

I have the wireless-info.txt file prepared if it would be helpful to extract any other info.

I am very new to linux and appreciate your help!

---

### Post by morrownr on 2024-03-25
Hi wascally314 

> iwconfig shows:

iwconfig was depreciated many years ago. I recommend you use 'iw'.

Post the results of:

$ iw dev

If it is not installed:

$ sudo apt install iw

Now to the issue:

This sounds like a case where Ubuntu has decided to use the 2.4 GHz band instead of the 5 or 6 GHz bands. Do your SSIDs all use the same name?

---

