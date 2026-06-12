---
title: "Suspend / resume problems in kubuntu 15.04"
date: 2015-06-06
forum: Networking &amp; Wireless
---

### Post by gavinspearhead2 on 2015-06-06
On resume from suspend (to memory) the wired network is usually (but not  always) not connected properly.   It has IP address, but it has no  default gateway. I have to manually   disconnect the network and  reconnect it. It uses DHCP through the   network manager.

Route shows something like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
```

Aftehr the reconnect the line gets added 
```
default         192.168.1.1    0.0.0.0         UG    100    0        0 eth0
```
and the network works again


I try to fix it by adding a script like this to /etc/pm/sleep.d, but it does'nt seem to get called.
```

#!/bin/sh
ase "${1}" in
        resume|thaw)
            nmcli d disconnect eth0
            nmcli d connect eth0
                         ;;
esac
exit 0
```

running this script manually with resume works fine and restores the network as it should.

Any thoughts on how to fix this problem?

On the previous version of Kubuntu it all worked fine.

---

