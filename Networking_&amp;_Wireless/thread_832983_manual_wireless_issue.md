---
title: "manual wireless issue"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by Kouran-sama on 2008-06-18
hi,
i read the sticky wireless configuration faq, the problem is, i have to manually connect to a ad-hoc node and get a dynamic ip address from that node.
when i try to "iwconfig wlan0 mode ad-hoc" on my computer it says "device or ressource busy" and fails to get the wlan in ad-hoc mode.
anyone got an idea what i'm doing wrong?

thanks in advance
tom

---

### Post by Ayuthia on 2008-06-18
> **Kouran-sama said:**
> hi,
i read the sticky wireless configuration faq, the problem is, i have to manually connect to a ad-hoc node and get a dynamic ip address from that node.
when i try to "iwconfig wlan0 mode ad-hoc" on my computer it says "device or ressource busy" and fails to get the wlan in ad-hoc mode.
anyone got an idea what i'm doing wrong?

thanks in advance
tom

Have you already done:
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 mode Ad-Hoc
...
```

---

### Post by Kouran-sama on 2008-06-18
thanks for your replay, this is what i was doing:

```

root@Azalea:~# ifconfig wlan0 down
root@Azalea:~# dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1d:e0:04:5b:eb
Sending on   LPF/wlan0/00:1d:e0:04:5b:eb
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 132.230.1.51 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
root@Azalea:~# ifconfig wlan0 up
root@Azalea:~# iwconfig wlan0 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.


```

hope this helps,....

---

### Post by Kouran-sama on 2008-06-18
found the solution. it workds for me if i leave the interface down while changing the modes and afterwards fire it up

---

### Post by mjaga on 2008-09-05
I had the same problem, but 

```
ifconfig wlan0 down
``` 

wasn't enough, I needed to 

```
ifconfig wlan0 0.0.0.0 down
```

before I could put my Intel wireless interface into ad-hoc mode.

---

