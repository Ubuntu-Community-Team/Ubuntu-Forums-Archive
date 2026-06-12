---
title: "Network interface reordering - dapper drake"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by mglauche on 2007-10-09
Hi,
  i got a little problem thats driving me quite insane. I got an amd64 machine with 2 NIC's (Both 3com 3c905B) running dapper drake.
Each time i reboot my ubuntu machine the network interfaces get randomly reordered, so i have
a 50% chance of a working setup. This is especially bad as the machine has a DHCP service running, which leaves the workstaions without network after a server reboot.

I did try to hardwire the settings in the interfaces file with specifying the MAC addresses, but no use.
My interfaces looks like this:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet static
        address 192.168.61.1
        hwaddress ether 00:10:5A:60:51:94
        netmask 255.255.255.0
        gateway 192.168.61.251
        post-up echo 1 > /proc/sys/net/ipv4/ip_forward

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth3
    iface eth3 inet manual
       hwaddress ether 00:01:02:E0:B1:04
    pre-up /sbin/ifconfig eth3 up # line maintained by pppoeconf

```

Also i have no real clue why ubuntu starts the NIC's at eth2, which probably does cause the trouble ..

---

### Post by spd106 on 2007-10-09
Use the /etc/iftab for setting persistent interface names.
e.g.
```
~$ cat /etc/iftab 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth2 mac 00:10:5A:60:51:94 arp 1
eth3 mac 00:01:02:E0:B1:04 arp 1
```

You may already have old entries in here for eth0 and eth1, it's ok to delete/replace them

---

### Post by mglauche on 2007-10-09
Thanks a lot ! This was exactly what i was looking for ! (unfortunately neither the interfaces nor the ifup man page did reference the /etc/iftab file, thats proably why i didn't find it in the first place)

---

