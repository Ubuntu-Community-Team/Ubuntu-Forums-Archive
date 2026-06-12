---
title: "'lo' interface has been renamed, how to revert?"
date: 2016-11-07
forum: Networking &amp; Wireless
---

### Post by donbowman on 2016-11-07
Using 16.10
I was trying to rename one of my usb ethernet interfaces using /etc/udev/rules.d/70-persistent-net.rules.
I put the mac address in there, on reboot the 'lo' interface was renamed instead.

I removed that rule, and rebooted, and now the lo remains renamed:

```
wd15: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 916  bytes 87894 (87.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 916  bytes 87894 (87.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

udevadm info -e is showing:

```
P: /devices/virtual/net/wd15
E: DEVPATH=/devices/virtual/net/wd15
E: ID_MM_CANDIDATE=1
E: ID_NET_LINK_FILE=/lib/systemd/network/99-default.link
E: IFINDEX=1
E: INTERFACE=wd15
E: SUBSYSTEM=net
E: SYSTEMD_ALIAS=/sys/subsystem/net/devices/wd15
E: TAGS=:systemd:
E: USEC_INITIALIZED=1312414

```


Does anyone have any suggestion? I did a 'grep -r wd15' /etc, /lib, /var, and I don't see anything.

---

### Post by Hadaka on 2016-11-07
Hi please post the output of..
```
lsb_release -a
ifconfig
cat /etc/udev/rules.d/70-persistent-net.rules
```
thanks.

---

### Post by donbowman on 2016-11-08
/etc/udev/rules.d/70-persistent-net.rules does not exist.


$ lsb_release -a
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.10
Release:	16.10
Codename:	yakkety


don@don-ux390:~$ ifconfig
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 0.0.0.0
        ether 02:42:fe:bb:12:20  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enx28f10e28285b: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.214.98  netmask 255.255.254.0  broadcast 192.168.215.255
        inet6 fe80::2e45:f49f:b7fd:afa  prefixlen 64  scopeid 0x20<link>
        ether 28:f1:0e:28:28:5b  txqueuelen 1000  (Ethernet)
        RX packets 871580  bytes 1135108454 (1.1 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 472507  bytes 124208011 (124.2 MB)
        TX errors 0  dropped 1 overruns 0  carrier 0  collisions 0


virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 00:00:00:00:00:00  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wd15: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 4477  bytes 417611 (417.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4477  bytes 417611 (417.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.243.132  netmask 255.255.254.0  broadcast 192.168.243.255
        inet6 fe80::b6f3:33b0:6e20:779e  prefixlen 64  scopeid 0x20<link>
        ether 00:c2:c6:f6:e6:9a  txqueuelen 1000  (Ethernet)
        RX packets 15169  bytes 2435281 (2.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1402  bytes 219303 (219.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

---

### Post by Hadaka on 2016-11-08
Hi , your docker entries i know nothing of... your other issue with lo being renamed
should be fixable with the attached link..note that the first answer states and gives an
example of the name change..which is " name= " "not kernel=". You must have either
upgraded from 14.04 to 16.10 or written your own udev rules...as udev rules were omitted
starting "i think" with ubuntu 15.10.   Here is the link.. I hope it helps as this is pretty much
the extent of my limited knowledge for udev..
*read the answer from Sebastian Marsching
[http://askubuntu.com/questions/767786/changing-network-interfaces-name-ubuntu-16-04](http://askubuntu.com/questions/767786/changing-network-interfaces-name-ubuntu-16-04)
Good Luck !

---

