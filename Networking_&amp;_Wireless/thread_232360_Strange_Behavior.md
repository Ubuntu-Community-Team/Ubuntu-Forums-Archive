---
title: "Strange Behavior"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by eldy on 2006-08-08
Using my laptop with Dapper installed; I can connect to a Netgear cable modem/router with WEP enabled, but not to a Linksys WRT54G with or without WEP enabled.

The Linksys is using firmware version 3.37.2 and the same laptop using Windows XP will connect with and without WEP.

Any suggestions?

```

iwconfig output
eth1   unassociated  ESSID:"linky"  Nickname:"ipw2100"
       Mode:Managed  Channel=0  Access Point: Not-Associated
       Bit Rate=0 kb/s   Tx-Power:off

```

---

### Post by eldy on 2006-08-08
dmesg gives the following:
```

[17179632.616000] ieee90211_crypt: registered algorithm 'WEP'
[17179732.916000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

---

