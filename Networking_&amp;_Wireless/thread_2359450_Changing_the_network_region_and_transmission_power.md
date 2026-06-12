---
title: "Changing the network region and transmission power of network adapter"
date: 2017-04-24
forum: Networking &amp; Wireless
---

### Post by shawn.c on 2017-04-24
Hey guys, 

I have an external wireless adapter, AWUS051NH v2 and I am trying to change the network region and transmission power of it. 
I have tried the command
```
iw reg set US
```
But i ended up with the results .
```
country 98: DFS-UNSET
```
Is there a way to edit the drivers / firmware of this adapter such that I can change the region and transmission power of this adapter. 

Thanks for your time.

---

### Post by shawn.c on 2017-05-30
Some updates and bump .

Right now the network adapter in question is

```
Bus 002 Device 003: ID 148f:3572 Ralink Technology, Corp. RT3572 Wireless Adapter
```

I have also found out that the driver it is using is currently 

```
rt2800usb
```

I have downloaded the backported drivers, more specifically backports 4.4.2-1 but I am not sure which file(s) I should be touching to set a static regulatory domain . 

Right now the problem I have is that even after editing the file /etc/default/crda to add in a country code , through dmesg I am seeing that cfg80211 forces a second update to override my user set region .

Thanks for your interest .

---

