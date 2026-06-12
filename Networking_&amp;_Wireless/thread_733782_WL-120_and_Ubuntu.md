---
title: "WL-120 and Ubuntu"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Shardana on 2008-03-24
Hello. I'm using Ubuntu 7.10 and want to use a Sitecom WL120V2 PCMCIA Wi-FI Card, but I have a problem. This wi-fi card isn't recognized by ubuntu. I've loaded the windows driver using ndiswrapper but the iwconfig command says:

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID: off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lspci

> 02:04.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)


What can I do to make it work properly?

---

