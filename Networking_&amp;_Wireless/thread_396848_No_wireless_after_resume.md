---
title: "No wireless after resume"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Serow225 on 2007-03-29
Hi all,

I've got a Compaq laptop running Edgy where I have wireless mostly working, and I'd appreciate your help resolving an issue involving suspend.

The laptop has a Broadcom 4306 card, and I'm using ndiswrapper. When I suspend and resume the laptop, I can't ping my router and thus don't have internet access. Stranger still, it seems to depend how long the laptop is suspended. If I suspend fora couple of minutes, things come up OK. If I suspend for an hour or two, the wireless light still comes on and then I have a few seconds of internet access before it stops working. If I then do a 'dhclient wlan0' or 'ifdown/ifup wlan0', things are back OK. 

I have added the line 'MODULES="ndiswrapper"' to /etc/default/acpi-support as suggested by another user, but it didn't help. My /etc/network/interfaces looks like this: 

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid XXX
wireless-key open YYY
```

I've attached the results of running netstat -rn at various times below:

Thanks for your help,
Eric

```

#normal operation, everything working
 netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

#immediately after resume
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

#few seconds after that, internet is working
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

#thirty seconds later, can't get to internet
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0

#then after manually running dhclient
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
```

---

### Post by H.E. Pennypacker on 2007-05-06
I am having the same problem.  Seriously, it's bizarre.  I believe it has something to do with ACPI.  I can't be sure, though.

Hopefully someone will be able to help us out.

---

