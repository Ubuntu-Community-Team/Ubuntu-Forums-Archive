---
title: "DNS question"
date: 2018-05-07
forum: Networking &amp; Wireless
---

### Post by moto1860 on 2018-05-07
I've changed IPv4 DNS with google's ones, under connection details I'm still reading IPv4 address: 192.168.1.2 is this normal? I'm asking cause the change isn't doing what is supposed to do.

edit: I suspect the ISP isn't allowing for such a change as I'm using a modem loaned by the ISP.

---

### Post by TheFu on 2018-05-08
For the most recent Ubuntu releases, Linux system have run a local caching DNS for most users. Could that be what you are seeing?

ISPs cannot control the settings on your Ubuntu system(s).  They can capture all DNS and redirect it to anywhere they like. My ISP used to do that, I complained, they made a change in the settings for my account that didn't trap DNS queries anymore and I was free to use whatever DNS provider I wished.   In their defence, DNS hijacking was a huge issue and they were just trying to prevent it for average users.  Their implementation wasn't very good, since NOT FOUND was redirected to some ad system they'd setup.

If you are using DHCP on your home computing devices, then the ISP can provide DNS servers to be used. That is part of the DHCP standards and usually necessary.  If you had your own router, it would do the same thing.

---

