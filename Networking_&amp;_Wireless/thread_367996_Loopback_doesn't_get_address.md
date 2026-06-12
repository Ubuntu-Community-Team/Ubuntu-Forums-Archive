---
title: "Loopback doesn't get address"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Schleproque on 2007-02-22
Good Day,

My machine is running Dapper using a tg3 driver that I had to compile and install by hand from source I got at the broadcom website.

I installed the machine using a usb ethernet adapter and switched over to the onboard after I compiled the new driver.

When the system boots up the loopback interface has no ip address. After I take the interface up and down using ifconfig it has the address of 127.0.0.1.

Any idea how I can fix this problem.

Thanks,
Rodney

---

### Post by gradedcheese on 2007-02-22
Weird.  Just to be sure, your /etc/network/interfaces file contains:

```

auto lo
iface lo inet loopback

```

right?

---

### Post by Schleproque on 2007-02-22
Yes it does.

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

---

