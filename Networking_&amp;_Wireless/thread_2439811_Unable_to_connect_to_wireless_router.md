---
title: "Unable to connect to wireless router"
date: 2020-04-01
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2020-04-01
I am running Ubuntu Desktop 18.  I have been unable to connect to the internet via my router.  I can ping my local router, but I can't do much of anything else.  
Here is what I get with my "route" command:
```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    0      0        0 <wireless_int>
default         _gateway        0.0.0.0         UG    20600  0        0 <wireless_int>
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 <wireless_int>
172.16.1.0     0.0.0.0         255.255.255.0   U     0      0        0 <wireless_int>
172.16.1.0     0.0.0.0         255.255.255.0   U     600    0        0 <wireless_int>
172.16.1.0     0.0.0.0         255.255.255.0   U     600    0        0 <wireless_int>
```

---

### Post by TheFu on 2020-04-01
i don't know much, but there should be only one gateway (not 2) and one local subnet route, not 3).  I&#8217;ve got no idea how the routing above happened.  Probably just too many connection attempts.

---

### Post by him610 on 2020-04-04
The information under columns 'Use Iface' is missing.

@TheFu - It could be that there two network devices in the system. Three local subnet route - no idea.

---

### Post by TheFu on 2020-04-04
> **him610 said:**
> The information under columns 'Use Iface' is missing.

@TheFu - It could be that there two network devices in the system. Three local subnet route - no idea.

Yep.  I've had multiple wifi devices connected and forgotten a few times myself. Perhaps one doesn't work well with the wifi-AP and the other one is a USB plug wifi adapter?

Hopefully, the OP got it all sorted.

---

