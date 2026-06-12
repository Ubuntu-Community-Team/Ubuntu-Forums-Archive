---
title: "Eratic Wifi"
date: 2016-11-20
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2016-11-20
Folks,

I;ve got a Toshiba laptop running 16.04 64 bit. My wifi is Realtek rtl8821ae and I am having disconnect issues.

Sometimes it is perfect and other times it drops out with a dmesg report as follows;

```
 43.402569] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   43.632194] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   43.640343] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   43.831081] r8169 0000:01:00.0 enp1s0: link down
[   43.831161] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   43.953855] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   47.013659] wlp2s0: authenticate with 74:da:38:12:fc:54
[   47.016814] wlp2s0: send auth to 74:da:38:12:fc:54 (try 1/3)
[   47.019439] wlp2s0: authenticated
[   47.022044] wlp2s0: associate with 74:da:38:12:fc:54 (try 1/3)
[   47.026774] wlp2s0: RX AssocResp from 74:da:38:12:fc:54 (capab=0x411 status=0 aid=4)
[   47.092229] wlp2s0: associated
[   47.092252] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   59.268665] ISO 9660 Extensions: Microsoft Joliet Level 3
[   59.275201] ISOFS: changing to secondary root
```

Oddly ifconfig shows my ethernet as enp1s0 and wlan as wlp2s0 which I've never seen before.

I've tried ```
service network-manager restart
``` with occasional success but nothing definite.

I've noticed similar problems posted for 15.10 with no obvious resolution.

Anyone any suggestions?

Geffers

---

### Post by Hadaka on 2016-11-20
Hi, you state..
"Oddly ifconfig shows my ethernet as enp1s0 and wlan as wlp2s0 which I've never seen before."
Starting with Ubuntu 15.10 new names were given to the old eth0 and wlan0.
your dmesg..
```
IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
```
Your wired and wireless connections are attempting to connect at the same time.
This can be avoided by unchecking the "Connect Automatically" box via an "Edit Connections"
Click your wifi signal icon >>Edit Connections>>Wireless>> Your SSID>> Edit and uncheck
Connect Automatically box.
save and close..then boot

---

### Post by Geoff_Lane on 2016-11-22
> **Hadaka said:**
> Hi, you state..

Your wired and wireless connections are attempting to connect at the same time.
This can be avoided by unchecking the "Connect Automatically" box via an "Edit Connections"
Click your wifi signal icon >>Edit Connections>>Wireless>> Your SSID>> Edit and uncheck
Connect Automatically box.
save and close..then boot

OK, done that and so far appears better.

Thanks,

Geoff

---

