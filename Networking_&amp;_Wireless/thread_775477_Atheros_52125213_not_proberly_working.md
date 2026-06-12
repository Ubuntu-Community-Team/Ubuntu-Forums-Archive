---
title: "Atheros 5212/5213 not proberly working"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by schierly on 2008-04-30
Hi, 
I have a strange problem with my D-Link AirPlus DWL-G650.

First my System:

Acer Travelmate 800,1,5GB RAM
Ubuntu Hardy, upgraded from gutsy, build in Intel Pro Wireless 2100B

I bought two additional brand new D-Link AirPlus DWL-G650 PCMCIA Cards.

Both cards are recognized as: (lspci)

```
03:00.0 Ethernet controller: Atheros Communications Inc.
 AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```

(iwconfig)
```

ath0      IEEE 802.11g  ESSID:"xxx"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:A4:9A:CB:B0   
          Bit Rate:6 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xx (WEP)   Security mode:restricted
          Power Management:off
          Link Quality=22/70  Signal level=-73 dBm  Noise level=-95 dBm
         **[COLOR="Red"] Rx invalid nwid:16980[/COLOR]**  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


and working fine, BUT with some problems:

1. In Hardy I get very high "Rx invalid nwid" values. The bit rate is also very low and switches very fast to 1Mbs. My built in Intel Pro Wireless 2100b card doesn't get this high values and is much faster than the Dlink.

---

