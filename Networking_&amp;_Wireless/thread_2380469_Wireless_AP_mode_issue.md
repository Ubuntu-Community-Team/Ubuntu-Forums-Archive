---
title: "Wireless AP mode issue"
date: 2017-12-18
forum: Networking &amp; Wireless
---

### Post by bern1 on 2017-12-18
Hi, 
I am trying to set up wireless Access Point on my new installed Ubuntu server 17.10. 
Hostapd starts ok. 
However i can't access internet from wifi DHCP hosts and don't know how could I fix this. 

I noticed that instead of 'IEEE 802.11abgn' iwconfig shows me 'IEEE 802.11'
```
ela@akacja:~$ iwconfig wlp4s0
wlp4s0    IEEE 802.11  Mode:Master  Tx-Power=18 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
I use [Qualcomm Atheros AR9380]("https://wikidevi.com/wiki/Atheros_AR5BXB112") Wireless Network Adapter.
```
ela@akacja:~$ sudo lshw -C network
.
.
.
       description: Wireless interface
       product: AR93xx Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 01
       serial: e4:ce:8f:52:c9:89
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.13.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:21 memory:91400000-9141ffff memory:91420000-9142ffff
```
Maybe there are something wrong with firmware?
Please advise how could I diagnose the issue. 
Any hint appreciated.
TIA

---

