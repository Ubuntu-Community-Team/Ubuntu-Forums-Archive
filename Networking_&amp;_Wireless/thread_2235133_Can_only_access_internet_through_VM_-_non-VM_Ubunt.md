---
title: "Can only access internet through VM - non-VM Ubuntu no longer has networking!"
date: 2014-07-19
forum: Networking &amp; Wireless
---

### Post by Bobby_James on 2014-07-19
I woke up today (GMT) and my networking has totally messed up.

I can connect to the router but that's it. I cannot access the router on 192,168.1.1, or ping, or use web, or email.

Ping informs me that the operation is not permitted.

I cannot ping my VM on the same 192.168.1.x network.

In short, I cannot do anything which involves networking.

I've rebooted and tried ifconfig wlan0 down / up. Doesn't work

How am I posting here? From Ubuntu in a Virtual Machine which works perfectly and accesses the internet as per usual.

Why? I have no idea. 

The problem is clearly not the router but something about my non-VM 12.04.

Can anyone provide advice? Is there a way to re-install networking easily?

---

### Post by praseodym on 2014-07-19
Please show:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
route -n
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
```

---

