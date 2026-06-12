---
title: "Intel Wireless 8260 connection drops after receiving channel switch event"
date: 2018-07-10
forum: Networking &amp; Wireless
---

### Post by pearpenguin on 2018-07-10
Hi all,

On a newly installed Xubuntu 18.04, I am able to connect to the internet via wireless adapter. But several times a day I get disconnected and won't be able browse any websites, however the WiFi status still shows as being connected to the AP. I see this type of message in the syslog whenever this happens:

```
 wpa_supplicant[907]: wlp2s0: CTRL-EVENT-CHANNEL-SWITCH freq=2412 ht_enabled=1 ch_offset=0 ch_width=20 MHz cf1=2412 cf2=0
```

Reconnecting to the AP doesn't fix the problem, only restarting NetworkManager will fix it.

Wireless info (obtained from after I have restarted NetworkManager): [http://paste.ubuntu.com/p/yw75nR3Yqm/](http://paste.ubuntu.com/p/yw75nR3Yqm/)

I have searched for wireless channel auto selection problems online without success. The wireless adapter seems to behave normally apart from this problem.
I have no access to the WiFI AP and cannot change it's configuration.
Any feedback or suggestions would be much appreciated,

Thanks in advance.

---

