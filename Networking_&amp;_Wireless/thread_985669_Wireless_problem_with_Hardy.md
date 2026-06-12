---
title: "Wireless problem with Hardy"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by Bluebell392 on 2008-11-17
I have a problem with the wireless, mainly it appears to connect, the start page for Ubuntu appears when I open Firefox, but any other site returns an error. The wireless card is a USB netgear WG111 V2. The output from dmesg | tail is as follows:```

[12326.132379] wlan1: Initial auth_alg=0
[12326.132388] wlan1: authenticate with AP 00:19:e4:46:1a:59
[12326.134795] wlan1: RX authentication from 00:19:e4:46:1a:59 (alg=0 transaction=2 status=0)
[12326.134800] wlan1: authenticated
[12326.134806] wlan1: associate with AP 00:19:e4:46:1a:59
[12326.137169] wlan1: RX AssocResp from 00:19:e4:46:1a:59 (capab=0x421 status=0 aid=1)
[12326.137174] wlan1: associated
[12326.137181] wlan1: switched to short barker preamble (BSSID=00:19:e4:46:1a:59)
[12326.139637] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[12336.221278] wlan1: no IPv6 routers present
[12371.360084] wlan1: deauthenticate(reason=3)

```

---

