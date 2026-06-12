---
title: "NDISwrapper stopped working after upgrading to Dapper"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by mgroat on 2006-10-16
After upgrading to Dapper my wireless network stopped working, I can't quite figure out why.  I am using a Linksys WMP54G with NDISwrapper 1.8.  I get the following results from "iwconfig"
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"GROAT"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"GROAT"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:09:5B:72:88:1A
          Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-69 dBm  Noise level:-212 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
(Note, rausb0 was added after I started having the problems, as a temporary solution)

Anybody have any ideas on what my problem could be?

---

