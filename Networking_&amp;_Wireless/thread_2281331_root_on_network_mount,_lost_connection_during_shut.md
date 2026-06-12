---
title: "root on network mount, lost connection during shutdown"
date: 2015-06-06
forum: Networking &amp; Wireless
---

### Post by tsabi2 on 2015-06-06
Hi,

please help me how to setup networking. My system root fs is on remote network mount (rbd in a ceph cluster), and my problem is during the shutdown the ubuntu drops the network connection and so the system lost it's root fs.

I have two ethernet adapters, joined in a bonding. I added a new initramfs script to setup bonding.

My kernel parameters:
```
ip=10.9.0.10::10.9.0.1:255.255.255.0:c10:bond0: bondslaves=eth1,eth0
```

my initramfs script (located in /etc/initramfs-tools/scripts/local-top dir):
```
#!/bin/sh

set -e

PREREQ=""

prereqs()
{
        echo "${PREREQ}"
}

case "${1}" in
        prereqs)
                prereqs
                exit 0
                ;;
esac

. /scripts/functions
wait_for_udev

echo "Network interfaces loaded: "
echo `ls /sys/class/net`

for x in $cmdline; do
    case $x in
    bondslaves=*)
            bondslaves="${x#bondslaves=}"
            ;;
    esac
done

IFS=","
for x in $bondslaves; do
    echo "+$x" > /sys/class/net/bond0/bonding/slaves
done

/sbin/route add default gw 10.9.0.1


```

and my /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual

auto bond0
iface bond0 inet manual

auto bond0:0
iface bond0:0 inet manual
        dns-nameservers 10.9.0.1
        up ip addr add 87.***.***.6/26 dev bond0 label bond0:0
        up ip addr add 87.***.***.3/26 dev bond0 label bond0:1
        up /sbin/route add default gw 87.***.***.1
        up /sbin/route del default gw 10.9.0.1


```

---

