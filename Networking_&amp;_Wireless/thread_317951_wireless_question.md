---
title: "wireless question"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by 200mg on 2006-12-13
I am using a WUSB54GP

When I do iwlist, I cannot see any essid's, however if i configure Kismet with any  source (ipw2100, rt2500, etc.)  I can see essid's.  How can I get iwlist to work?

```
eth2      IEEE 802.11b  ESSID:off/any  
          Mode:Monitor  Channel=9  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
iwlist eth2 scan
eth2      No scan results

```

I can also capture packets with kismet and weplab so I know the card is working, i just can't get iwlist scan to show me the essid's.  TIA for any help

---

