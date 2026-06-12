---
title: "Ad Hoc - Vista &lt;&lt;&lt;&gt;&gt;&gt;&gt; Ubuntu"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Liorx on 2007-03-22
I am trying for days to establish an Ad Hoc connection 
Between my Vista PC to my kubuntu laptop.
I am using Knetworkmanager  and I tried several times to edit the \etc\ network\interfaces to use static I.P on Ad Hoc mode, I receive a signal from vista PC but can't establish connection.  

I easily connect to other  wireless networks that provide IP throw DHCP.
note: both my  wi-fi cards support Ad Hoc mode

Please help!

(etc\network\interfaces configuration will be helpful)  Thanks

---

### Post by spd106 on 2007-03-22
I haven't much experience with Vista yet, but you should be okay as long as both machines are on the same subnet.

Try putting one on 192.168.5.1 and the other on 192.168.5.2, both with a subnet mask of 255.255.255.0. There should not be any need to set the gateway. The interfaces file will probably look like this, assuming there's no encryption.
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.5.2
netmask 255.255.255.0

```

---

