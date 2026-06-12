---
title: "Wrong Wireless protcol installed"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by clown99 on 2007-01-19
Hi,

have installed the ndiswrapper with the wlan win-drivers. So far its good configured, but the protocol is on 11g, it has to be 11b. Maybe, thats the problem of conn-probz.

If I tip iwconfig, I get

wlan0 IEEE 802.11g ESSID:"Bennis Exnetz"
Mode:Managed Frequency:2.447 GHz Access Point: 00:30:F1:A5:0B8
Bit Rate:11 Mb/s Tx-Power:10 dBm Sensitivity=0/3
RTS thr:4096 B Fragment thr:4096 B
Encryption key:"..." Security mode:restricted
Power Managementff
Link Quality:37/100 Signal level:-72 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

but the router is configured for 11b and my wlan-driver also supports that standard.

Somebody got an answer how to change or what else to do???
Edit/Delete Message

---

### Post by clown99 on 2007-01-20
Friend an me have solved it.

The problem was the WEP-Config. it was configured for WEP 3, under WEP 1 it wokrs.

Thank you noncheckers.

---

