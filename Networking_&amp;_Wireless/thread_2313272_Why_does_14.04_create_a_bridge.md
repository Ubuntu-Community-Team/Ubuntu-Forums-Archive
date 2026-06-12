---
title: "Why does 14.04 create a bridge?"
date: 2016-02-11
forum: Networking &amp; Wireless
---

### Post by Hammi on 2016-02-11
Hi,

I have a new Ubuntu install of 14.04.3 server on a Supermicro X10SRL-F board. I also have an Intel X540 T1 card in the system (which is the one to be used - onboard LAN is not needed for now).

The fresh Ubuntu install - no config applied - as well as my current config (with a static IP) always give me a bridge on top of what I have created. I cannot understand why and how to stop that. I will need a bridge at some point, but not the "empty one" (no adapters associated) that ubuntu creates.

/etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p3p1
iface p3p1 inet dhcp

```

alternative /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto p3p1
# iface p3p1 inet dhcp

auto p3p1
iface p3p1 inet static
    address 192.168.67.74
    netmask 255.255.255.0
    network 192.168.67.0
    broadcast 192.168.67.255
    gateway 192.168.67.1
    dns-nameservers 192.168.67.100 192.168.67.104 192.168.89.29
    dns-search example.com
    dns-domain example.com
```

ifconfig shows:
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:176 (176.0 B)  TX bytes:176 (176.0 B)

p3p1      Link encap:Ethernet  HWaddr a0:36:9f:66:a8:1c
          inet addr:192.168.67.74  Bcast:192.168.67.255  Mask:255.255.255.0
          inet6 addr: fe80::a236:9fff:fe66:a81c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:488 errors:0 dropped:16 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:40960 (40.9 KB)  TX bytes:24388 (24.3 KB)

virbr0    Link encap:Ethernet  HWaddr da:a1:7e:cd:69:5d
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

brctl show:
```
bridge name     bridge id               STP enabled     interfaces
virbr0          8000.000000000000       yes
```

brctl show virbr0:
```
bridge name     bridge id               STP enabled     interfaces
virbr0          8000.000000000000       yes
```
(shouldn't there be more info on the bridge here?)

I'm tempted to remove the link to bridge in /etc/network/if-pre-up.d to get rid of this bridge. But I'm sure there must be a better way.

Thanks for any hint!

---

### Post by Doug S on 2016-02-11
That is the default bridge when one installs virtualisation, either during initial installation or afterwards. It will have also created some default iptables rules to allow any subsequently created default VM's to communicate.

Myself, I just left it there, and then created a "real" bridge so that my VMs could be on my main LAN sub-net.

---

### Post by collisionystm on 2016-02-11
Do you have virtualization enabled? You can remove the bridge from within virsh.

> virsh

net-info default

Example output:

virsh # net-info default
Name:           default
UUID:           7af50021-c70b-4ca2-86ab-55d
Active:         yes
Persistent:     yes
Autostart:      yes
Bridge:         virbr0

Remove with

> net-destroy default


---

### Post by Hammi on 2016-02-22
Yes, thanks. It appears that this was indeed related to virtualization. It didn't do that the last time I installed my virtualization host - but I have to admit, that was years ago. :D

---

