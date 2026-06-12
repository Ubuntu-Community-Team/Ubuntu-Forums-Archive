---
title: "Wireless Card not detected"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by ububug on 2007-12-09
I'm using a Dynex wireless pci desktop card on a dapper and when I enter ```
lspci
```, I see

```
0000:05:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller(rev 02)
```

however, the wlan pci card doesn't show up in System->Administration->Networking

and when I enter ```
iwconfig
```

I just see

```
lo        no wireless extensions

eth0      no wireless extensions

eth1      no wireless extensions

sit0      no wireless extensions
```

I have no idea what's going on and any help would be great.

---

### Post by rustybronco on 2007-12-09
> **ububug said:**
> I'm using a Dynex wireless pci desktop card on a dapper and when I enter ```
lspci
```, I see

```
0000:05:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller(rev 02)
```

however, the wlan pci card doesn't show up in System->Administration->Networking

and when I enter...

I have no idea what's going on and any help would be great. I believe that chipset won't work natively in 6.10 and back, there are methods listed on this forum, maybe you could give them a try, or you download a live cd of 7.10, I know that card works with it.

---

### Post by ububug on 2007-12-09
> **rustybronco said:**
> I believe that chipset won't work natively in 6.10 and back, there are methods listed on this forum, maybe you could give them a try, or you download a live cd of 7.10, I know that card works with it.

It used to show up before, and I had downloaded the drivers with ndiswrapper, but it just stopped showing up today.

---

