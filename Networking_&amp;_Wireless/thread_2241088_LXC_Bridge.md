---
title: "LXC Bridge"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by elysian2 on 2014-08-24
I have been using Arch Linux as my desktop for a while now. This week the Linux Foundation announced the certification program which I applied for so I've been brushing up on my Ubuntu since I haven't used it after jumping to Arch a week after switching to Linux. I was watching the CBT Nuggets Ubuntu series which mentioned containers so I thought I would try it in Ubuntu. LXC through br0 works fine on my desktop but I could not seem to get the Ubuntu LXC to connect to another other interface besides the default lxcbr0 in 14.04 server.

[COLOR=#ff0000][SIZE=4]Arch Desktop[/SIZE][/COLOR]

```
 
NAME          STATE    IPV4         IPV6  AUTOSTART  
---------------------------------------------------
backup        STOPPED  -            -     NO         
monitorix     RUNNING  192.168.1.7  -     NO         
owncloud      RUNNING  192.168.1.5  -     NO         
transmission  RUNNING  192.168.1.6  -     NO

```

```

br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.1  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::4912:bbd3:80f0:6027  prefixlen 64  scopeid 0x20<link>
        inet6 fe80::6a05:caff:fe14:78c0  prefixlen 64  scopeid 0x20<link>
        ether 68:05:ca:14:78:c0  txqueuelen 0  (Ethernet)
        RX packets 10196  bytes 11789002 (11.2 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8005  bytes 1148450 (1.0 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp2s0: flags=4419<UP,BROADCAST,RUNNING,PROMISC,MULTICAST>  mtu 1500
        inet6 fe80::f5d1:e556:2bfc:762d  prefixlen 64  scopeid 0x20<link>
        inet6 fe80::6a05:caff:fe14:78c0  prefixlen 64  scopeid 0x20<link>
        ether 68:05:ca:14:78:c0  txqueuelen 1000  (Ethernet)
        RX packets 45666  bytes 61669764 (58.8 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 31433  bytes 3341466 (3.1 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  memory 0xf73c0000-f73e0000  

```

```

Description="Bridge connection"
Interface=br0
Connection=bridge
BindsToInterfaces=(enp2s0)
IP=static
Address=('192.168.1.1/24')
Gateway='192.168.1.254'
DNS=('192.168.1.254')

```

```

lxc.mount = /var/lib/lxc/owncloud/fstab
lxc.tty = 1
lxc.pts = 1024
lxc.stopsignal = 38
lxc.kmsg = 0
lxc.autodev = 1
lxc.cgroup.devices.deny = a
lxc.cgroup.devices.allow = c *:* m
lxc.cgroup.devices.allow = b *:* m
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
lxc.cgroup.devices.allow = c 1:7 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 4:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:2 rwm
lxc.cgroup.devices.allow = c 136:* rwm
lxc.utsname = test
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = br0
lxc.network.name = eth0
lxc.network.mtu = 1500
lxc.network.ipv4.gateway = 192.168.1.254
lxc.network.ipv4 = 192.168.1.5/24
lxc.cap.drop = sys_module
lxc.cap.drop = mac_admin
lxc.cap.drop = mac_override
lxc.cap.drop = sys_time
lxc.rootfs = /var/lib/lxc/owncloud/rootfs
lxc.cgroup.memory.limit_in_bytes = 50M
lxc.cgroup.memory.memsw.limit_in_bytes = 76M
lxc.cgroup.cpuset.cpus = 0

```

[SIZE=4][COLOR=#ff0000]Ubuntu Server Host[/COLOR][/SIZE]

```

auto br0
iface br0 inet static
address 192.168.2.20
gateway 192.168.2.254
netmask 255.255.255.0
dns-nameserver 192.168.2.254
dns-nameserver 192.168.1.254
bridge_ports eth0

```

```

br0       Link encap:Ethernet  HWaddr 08:00:27:6a:ca:51  
          inet addr:192.168.2.20  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe6a:ca51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12704 (12.7 KB)  TX bytes:4225 (4.2 KB)

eth0      Link encap:Ethernet  HWaddr 08:00:27:6a:ca:51  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9898 (9.8 KB)  TX bytes:9509 (9.5 KB)

```

```

ping -I br0 google.ca
PING google.ca (173.194.33.143) from 192.168.2.20 br0: 56(84) bytes of data.
64 bytes from sea09s17-in-f15.1e100.net (173.194.33.143): icmp_seq=1 ttl=57 time=10.5 ms
64 bytes from sea09s17-in-f15.1e100.net (173.194.33.143): icmp_seq=2 ttl=57 time=10.8 ms
64 bytes from sea09s17-in-f15.1e100.net (173.194.33.143): icmp_seq=3 ttl=57 time=10.6 ms

```

[SIZE=4][COLOR=#ff0000]**Ubuntu LXC**[/COLOR][/SIZE]

The container would not start with no static LXC IP and DHCP, or there would be no connection with static LXC IP and no DHCP in /var/lib/lxc/ubuntu/rootfs/etc/network/interfaces

```

lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = br0
lxc.network.name = eth0
lxc.network.mtu = 1500
lxc.network.ipv4.gateway = 192.168.2.254
lxc.network.ipv4 = 192.168.2.50/24

```

I did everything pretty much the same in Ubuntu as in Arch so is there something I'm missing?

---

