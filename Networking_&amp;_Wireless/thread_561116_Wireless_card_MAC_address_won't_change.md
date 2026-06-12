---
title: "Wireless card MAC address won't change"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by Clang on 2007-09-27
Hi all,

I'm having trouble changing the mac address of my wireless card (RT61 chipset).

I have tried macchanger and 

$ ifconfig ra0 down
$ ifconfig ra0 hw ether 00:00:00:00:00:01
$ ifconfig ra0 up

and neither work.

In the second case the mac address gets changed but when the interface is put back up the address reverts to the original.

I do not have this problem when I change the address of eth0.

I added the line to /etc/iftab and that did nothing.

I can't find anything about ra0 in /etc/network/interface.. although it does list ath0 (different chipset?) and wlan0, which I can't find reference to anywhere else on my system.

Is this something to do with the driver? Any help would be much appreciated.

Thanks

---

### Post by lisati on 2007-09-27
The MAC address is usually built into the hardware when it is manufactured - are you trying to over-ride it?

---

### Post by Clang on 2007-09-27
Yes, I need to override my mac address in software.

---

### Post by netztier on 2007-09-27
> **Clang said:**
> Yes, I need to override my mac address in software.

I've been trying this also - it used to work with dapper, but stopped to work with edgy.
My notebook has a ...
```
marc@torch:~$** lspci**
...
02:04.0  Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
...
```

.. which is used with the modules from the restricted-modules package.

Since edgy, macchanger would accept the command, but sniffing with kismet in parallel on another notebook showed that any frame coming from this NIC still used the original MAC address.

I then found another solution in that particular situation (combination of a WLAN router and a WLAN AP in "client mode" which allowed MAC override), so I've stopped investigating on the why and hows.

regards

Marc

---

