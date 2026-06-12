---
title: "No iwlist scan results for ath0!"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by rocketman768 on 2008-11-15
So, for a long time I have been using "iwlist scan" to see the available networks around me with my ath0 interface (06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)). Without installing or upgrading anything, today it won't give any results at all:

```

philip@pglap:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results


```

I am using 8.04, and kernel 2.6.24-21-386, and the madwifi drivers that came with it. The interface is there and I can change the essid and all that with iwconfig, but I just don't get any scan results. WTF mate?

---

### Post by rocketman768 on 2008-11-15
I'm retarded. There was a tiny switch on the laptop that disables the radio, and it was flipped.

---

