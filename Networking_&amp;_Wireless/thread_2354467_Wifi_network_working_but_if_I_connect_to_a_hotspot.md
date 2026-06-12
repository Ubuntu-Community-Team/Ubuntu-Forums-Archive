---
title: "Wifi network working but if I connect to a hotspot from mobile interet not working"
date: 2017-03-03
forum: Networking &amp; Wireless
---

### Post by Akshay_Jain on 2017-03-03
Hi,

If I connect to the Wifi network provided by our college, everything works fine.
But, when I connect to a hotspot network from my Android phone, it gets connected but I am not able to open any webpage.

When I connect to the college Wifi and run ifconfig I get the following output:

```

wlan0  inet addr:192.168.21.47  Bcast:192.168.31.255  Mask:255.255.240.0
          inet6 addr: fe80::6a94:23ff:fe04:9fb7/64 Scope:Link
          
```

When I connect to the mobile hotspot I get the following output:

```

wlan0             inet addr:192.168.43.102  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::6a94:23ff:fe04:9fb7/64 Scope:Link

```

Is it due to the change in IP address?

Please help.

Thanks,
Akshay

---

### Post by Keith_Helms on 2017-03-05
I assume you don't have your phone in airplane mode.   What does the command iwconfig show when you're connected to the hotspot?

---

