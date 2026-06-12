---
title: "Network Device unmanaged on Ubuntu 16.10 Server (using NM) usual fix not working"
date: 2017-03-03
forum: Networking &amp; Wireless
---

### Post by darkgod on 2017-03-03
Hello, 
I have done this already on Ubuntu 16.04 Server install and it worked fine.
Today i had to do this on Ubuntu 16.10 server install. 
Unfortunately This time it didnt work.
I removed all but local interface from the classical network configuration. Added manged=true to the NM configuration.
However the Ethernet devices show up as unmanaged.

This is what i have:
$ cat /etc/network/interfaces
[SIZE=3]```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

```[/SIZE]

cat /etc/NetworkManager/NetworkManager.conf 
```
[SIZE=3][main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true[/SIZE]
```

and if i issue:
ifconfig -a
```
[SIZE=3]enp0s31f6: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether c8:d3:ff:27:61:24  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xd4300000-d4320000  

enp68s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether c8:d3:ff:91:18:78  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 28766  bytes 4298663 (4.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 28766  bytes 4298663 (4.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.142.82.191  netmask 255.0.0.0  broadcast 10.255.255.255
        inet6 fe80::f2c3:f21a:3639:f465  prefixlen 64  scopeid 0x20<link>
        ether f0:d5:bf:12:7a:0a  txqueuelen 1000  (Ethernet)
        RX packets 362501  bytes 428689582 (428.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 177375  bytes 32944050 (32.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
[/SIZE]
```

I started installing a ubunu 16.10 server on a hp Zbook with thunderbolt3 docking station connected (network connection on enp68s0) and from there i installed i3 with X-server and ppa nvidia drivers, intel-microcode
Then i removed "enp68s0" from networking and installed nm.

I wonder how the nm decides if the resource is managed or not ? (i am using Network Manager 1.2.6)

I also tried to configure one of the network interfaces in the old classical wa and then set the managed=true , but still nothing.

---

