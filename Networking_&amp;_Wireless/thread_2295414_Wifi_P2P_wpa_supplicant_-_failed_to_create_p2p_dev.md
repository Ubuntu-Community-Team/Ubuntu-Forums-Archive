---
title: "Wifi P2P wpa_supplicant - failed to create p2p device interface"
date: 2015-09-18
forum: Networking &amp; Wireless
---

### Post by Giacomo_Atzeni on 2015-09-18
[SIZE=2][FONT=arial]Hello, 
[/FONT][/SIZE][LEFT][SIZE=2][FONT=arial][COLOR=#111111]I'm trying to configure wifi p2p connection with ubuntu, but I have some issues. In particular I followed this [guide]("http://riya80211.blogspot.de/2013/07/p2p-configuration-of-wpasupplicant-in.html") and this [one]("https://wireless.wiki.kernel.org/en/developers/p2p/howto")[/COLOR][COLOR=#111111].
Almost everything seems ok, but when I lunch the command:[/COLOR][/FONT][/SIZE]
```
[FONT=courier new]sudo ./wpa_supplicant -i wlan0 -c /etc/p2p.conf -Dnl80211 -ddt[/FONT]
```

[SIZE=2][FONT=arial][COLOR=#111111]I get this error:[/COLOR][/FONT][/SIZE]
[/LEFT]
```
[SIZE=2][FONT=arial][FONT=courier new]1442591346.069280: nl80211: Set wlan0 operstate 0->0 (DORMANT)
     1442591346.069563: netlink: Operstate: ifindex=4 linkmode=-1 (no change), operstate=5 (IF_OPER_DORMANT)
     1442591346.069901: nl80211: Create interface iftype 10 (P2P_DEVICE)
     1442591347.591372: Failed to create interface p2p-dev-wlan0: -5 (Input/output error)
     1442591347.592233: nl80211: Failed to create a P2P Device interface p2p-dev-wlan0
     1442591347.593031: P2P: Failed to create P2P Device interface
     1442591347.593754: P2P: Failed to enable P2P Device interface
     1442591347.594689: EAPOL: disable timer tick
     1442591347.595501: random: Got 20/20 bytes from /dev/random[/FONT]
[/FONT][/SIZE]
```[LEFT][SIZE=2][FONT=arial][COLOR=#111111]After that, if I open anyway another shell and I type[/COLOR][/FONT][/SIZE]
```
[FONT=courier new][SIZE=2]sudo ./wpa_cli -i wlan0[/SIZE][/FONT]
```

[SIZE=2][FONT=arial][COLOR=#111111]the session seems to start correctly, but when I try to use p2p commands, they fail:[/COLOR][/FONT][/SIZE]
[/LEFT]
```
 [SIZE=2][FONT=arial]     [FONT=courier new]wpa_cli v2.4
     Copyright (c) 2004-2015, Jouni Malinen <j@w1.fi> and contributors
     This software may be distributed under the terms of the BSD license.
     See README for more details.
     Interactive mode
     > p2p_find
     FAIL[/FONT]
[/FONT][/SIZE]
```[LEFT][COLOR=#111111][FONT=Ubuntu][SIZE=2][FONT=arial]Someone can help me? I'm using a WANDBOARD quad device with Ubuntu 14.04.2 LTS. I can't figure out why P2P interface cannot be created. Thank you.[/FONT][/SIZE]
[/FONT][/COLOR][/LEFT]

---

