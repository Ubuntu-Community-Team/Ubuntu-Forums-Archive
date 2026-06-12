---
title: "What happened to my networking?"
date: 2019-09-29
forum: Networking &amp; Wireless
---

### Post by spookybathtub on 2019-09-29
Hello.  I have an HTPC running Ubuntu 16.04.  After a few months of being powered off, I turned it on today and noticed it didn't get an IP address.  Weird.  Running **dhclient eth0** works right away and life is good.  But this happens again after every reboot.  I noticed **ifup** was also not working so I checked /etc/network/interfaces and the interface is missing:

```
$ # /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

That's weird.  This had been working for years before.  So I tried adding a line:
```
iface eth0 inet dhcp
```

Now after rebooting, I still don't have an IP, and ifup gives an error:
```

# ifup -v eth0
Configuring interface eth0=eth0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant


/sbin/dhclient -1 -v -pf /run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -I -df /var/lib/dhcp/dhclient6.eth0.leases eth0     
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Usage: dhclient [-4|-6] [-SNTP1dvrx] [-nw] [-p <port>] [-D LL|LLT]
                [-s server-addr] [-cf config-file] [-lf lease-file]
                [-pf pid-file] [--no-pid] [-e VAR=val]
                [-sf script-file] [interface]
Failed to bring up eth0.

```
This looks like a bug with ifup because the dhclient man page does on this system not show any **-I** option.  ifup is version 0.8.10ubuntu1.4.

---

### Post by spookybathtub on 2019-09-30
Ok this is solved after upgrading all packages with apt.  I think maybe an update was partially installed.  I also added a line **auto eth0**&#8203; and now it starts at boot.

---

