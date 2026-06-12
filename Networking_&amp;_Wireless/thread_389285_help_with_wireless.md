---
title: "help with wireless"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by d80tb7 on 2007-03-20
Hello All.  Complete newbie here so  go easy :)

I'm running Edgy AMD64 and have most things working apart from my wireless.  The card itself uses a Ralink 2500 chip which I believe is supported.

Lspci says: Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)


I can do ifconfig ra0 which gives me:

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:57:9C:4E  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0xc000 

However I can't for the life of me work out how to connect to my wireless network.  Enabling wireless in administration -> networking doesn't seem to do anything and scanning with wifi-radar doesn't show any networks either.  I've turned off any encryption on the network and if I boot into windows I can connect to the network just fine.


All help gratefully recieved!

Chris

---

### Post by chili555 on 2007-03-20
Please let us see the results of:```
sudo iwconfig ra0
iwlist ra0 scan
```Thanks. We'll get it.

---

### Post by d80tb7 on 2007-03-20
Ok here we go.

sudo iwconfig ra0
Password:
ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=1 Mb/s   Tx-Power:0 dBm   
          RTS thr: off   Fragment thr: off
          Encryption key: off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwlist ra0 scan
ra0       No scan results


Chris

---

