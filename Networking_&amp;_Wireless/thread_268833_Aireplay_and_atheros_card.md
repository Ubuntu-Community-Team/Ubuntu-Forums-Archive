---
title: "Aireplay and atheros card"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by unLog!c on 2006-09-30
I have D-Link DWL-G650 rev. C3 wireless card with Atheros chipset (patched Madwifi drivers)...
It supports packet injection and its working... Im testing my home network and network at workplace, but in airodump IVs are not collected as fast they should be..

I get about 1000 IVs in 12sec... Aireplay is working and injection (ARP request replay) but, when i run wireshark I can see this while scaning my ath0 wireless interface:
```
348966 Siemens_58:3e:c2 -> Broadcast    IEEE 802.11 Beacon frame,SN=3317,FN=0,BI=100, SSID: "unlogic"[Malformed Packet]
 33.353273              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.354314 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3318,FN=0
 33.373270              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.374769 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3319,FN=0
 33.392768 Shuttle_24:9f:3a -> 01:00:5e:7f:ff:fa IEEE 802.11 Data,SN=3320,FN=0
 33.413220              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.414344 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3322,FN=0
 33.433215              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.434252 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3323,FN=0
 33.451372 Siemens_58:3e:c2 -> Broadcast    IEEE 802.11 Beacon frame,SN=3324,FN=0,BI=100, SSID: "unlogic"[Malformed Packet]
 33.453269              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.454294 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3325,FN=0
 33.474235              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.475272 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3326,FN=0
 33.493239              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.494339 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3327,FN=0
 33.513221              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.514266 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3328,FN=0
 33.533223              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.534269 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3329,FN=0
 33.553776 Siemens_58:3e:c2 -> Broadcast    IEEE 802.11 Beacon frame,SN=3330,FN=0,BI=100, SSID: "unlogic"[Malformed Packet]
 33.554300              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.555319 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3331,FN=0
 33.573263              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.574295 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3332,FN=0
 33.593223              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.594272 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3333,FN=0
 33.613229              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.614321 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3334,FN=0
 33.633229              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.634279 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3335,FN=0
 33.653967              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.655045 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3336,FN=0
 33.656327 Siemens_58:3e:c2 -> Broadcast    IEEE 802.11 Beacon frame,SN=3337,FN=0,BI=100, SSID: "unlogic"[Malformed Packet]
 33.673972              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.675017 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3338,FN=0
 33.693273              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.694313 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3339,FN=0
 33.713245              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.714335 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3340,FN=0
 33.733255              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.734297 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3341,FN=0
 33.754247              -> IntelCor_66:65:b1 (RA) IEEE 802.11 Acknowledgement
 33.755270 IntelCor_66:65:b1 -> Broadcast    IEEE 802.11 Data,SN=3342,FN=0
 33.758590 Siemens_58:3e:c2 -> Broadcast    IEEE 802.11 Beacon frame,SN=3343,FN=0,BI=100, SSID: "unlogic"[Malformed Packet]

```

Note Siemmens_58:3e:c2 is my router (Siemens SE555) and IntelCor_66:65:b1 is my other wifi card (intel pw3945 that is client im using in attack)

Im new to linux and I have followed this tutorial for getting all stuff ready:
[http://www.turkeyfarm.net/blog/2006/06/22/cracking-wep-with-linux-actually-works/](http://www.turkeyfarm.net/blog/2006/06/22/cracking-wep-with-linux-actually-works/)

I searched google for those malformed packets, but so far no luck :(


Please help me..

---

### Post by tturrisi on 2006-10-01
google again:
[http://www.google.com/search?hl=en&q=wireshark+malformed+packets&btnG=Google+Search](http://www.google.com/search?hl=en&q=wireshark+malformed+packets&btnG=Google+Search)

---

