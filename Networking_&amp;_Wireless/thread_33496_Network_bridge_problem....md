---
title: "Network bridge problem..."
date: 2005-05-11
forum: Networking &amp; Wireless
---

### Post by stefanorg on 2005-05-11
Hi all!

I'm new to ubuntu (i come from a gentoo box)...i've two NIC (working) and i need to set-up a bridge, so i've modified the /etc/network/interfaces like this:

```

iface eth0 inet static
        address 0.0.0.0

iface eth1 inet static
        address 0.0.0.0


iface br0 inet static
        bridge_ports all
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 212.216.112.112
        address 192.168.0.3

auto br0
```

I need that the br0 have the 192.168.0.3 address, all working fine but when i try to shutdown the network or reboot the pc i receive this message in loop

```
unregister_netdevice: waiting for br0 to become free. Usage count = 1
```

and the only solution is to press the reset button.

This is the /sbin/ifconfig output:

```

br0       Link encap:Ethernet  HWaddr 00:10:5A:B3:AC:1C
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:feb3:ac1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3144285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1787621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4468674974 (4.1 GiB)  TX bytes:133586344 (127.3 MiB)

eth0      Link encap:Ethernet  HWaddr 00:11:D8:13:40:13
          inet6 addr: fe80::211:d8ff:fe13:4013/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3144285 errors:3 dropped:0 overruns:0 frame:3
          TX packets:1787626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4512695342 (4.2 GiB)  TX bytes:133586722 (127.3 MiB)
          Interrupt:21 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:10:5A:B3:AC:1C
          inet6 addr: fe80::210:5aff:feb3:ac1c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b)
          Interrupt:17 Base address:0xbc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1121502 (1.0 MiB)  TX bytes:1121502 (1.0 MiB)

```

Any suggestion?

Thanks.

Stefano

---

### Post by stefanorg on 2005-05-11
No one?1?!?

---

### Post by stefanorg on 2005-05-14
Hi hope this is usefull....

i've find an initi script in [http://www.tldp.org/HOWTO/BRIDGE-STP-HOWTO/index.html](http://www.tldp.org/HOWTO/BRIDGE-STP-HOWTO/index.html)

i've modified the script for my own use and i've installed the service in the runlevel :

```

sudo cp bridge.sh /etc/initi.d/
update-rc.d bridge.sh defaults
#removing the default network script
update-rc.d -f netoworking remove

```

This is the script modified by me:
```

#! /bin/bash
# Copyright (c) 2000 Uwe Böhme.  All rights reserved.
#
# Author: Uwe Böhme <uwe@bnhof.de>, 2000
#
#
# /sbin/init.d/bridge
#

#. /etc/rc.config

return=$rc_done
case "$1" in

    start)
        echo "Starting service bridge br0"
        brctl addbr br0  ||  return=$rc_failed
        brctl setbridgeprio br0 0 || return=$rc_failed
        brctl addif br0 eth0  ||  return=$rc_failed
        brctl addif br0 eth1  ||  return=$rc_failed
        ifconfig eth0 0.0.0.0  ||  return=$rc_failed
        ifconfig eth1 0.0.0.0  ||  return=$rc_failed
        ifconfig br0 192.168.0.3 netmask 255.255.255.0  ||  return=$rc_failed
        brctl sethello br0 1  ||  return=$rc_failed
        brctl setmaxage br0 4  ||  return=$rc_failed
        brctl setfd br0 4  ||  return=$rc_failed

        echo -e "\t Setting Route..."
        route add default gw 192.168.0.1 || return=$rc_failed

        echo -e "$return"
        ;;

    stop)
        echo "Shutting down service bridge mueb"
        ifconfig eth1 down    ||  return=$rc_failed
        ifconfig eth0 down    ||  return=$rc_failed
        ifconfig br0 down     ||  return=$rc_failed
        brctl delif br0 eth1  ||  return=$rc_failed
        brctl delif br0 eth0  ||  return=$rc_failed
        brctl delbr br0  ||  return=$rc_failed
        rmmod bridge || return=$rc_failed

        echo -e "$return"
        ;;

    status)
        ifconfig br0
        brctl show br0
        ;;

    restart)
        $0 stop && $0 start || return=$rc_failed
        ;;

    *)
        echo "Usage: $0 {start|stop|status|restart}"
        exit 1
esac

test "$return" = "$rc_done" || exit 1
exit 0


```

---

### Post by kestasjk on 2006-06-11
Just replying to say I found this useful, thanks.

---

