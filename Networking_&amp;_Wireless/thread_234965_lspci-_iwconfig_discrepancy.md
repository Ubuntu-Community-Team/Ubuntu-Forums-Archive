---
title: "lspci- iwconfig discrepancy"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by stevieb on 2006-08-12
hello,

having trouble getting my broadcom 4319 working.  did the ndiswrapper thing in accordance with the howto listed here, but while lspci lists it as:

```
0000:01:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)

```

iwconfig lists:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"STSN"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:03:52:E7:60:C0
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```

does this matter, or is the problem something else?

-steve

---

