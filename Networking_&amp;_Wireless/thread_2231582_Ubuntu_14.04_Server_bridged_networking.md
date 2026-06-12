---
title: "Ubuntu 14.04 Server bridged networking"
date: 2014-06-26
forum: Networking &amp; Wireless
---

### Post by Manas B on 2014-06-26
Hello, I am trying to set up bridged networking on Ubuntu Server 14.04 for use with KVM virtualization. I am following the instructions located here: [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

At the point where the instructions say to stop networking, this is what I get:
```

> sudo invoke-rc.d networking stop
stop: Job failed while stopping
invoke-rc.d: initscript networking, action "stop" failed.
```
Trying to restart it does not work either, it fails with a similar message.

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto p6p1
#iface p6p1 inet dhcp
iface p6p1 inet static
address 192.168.0.130
netmask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.0.255
dns-nameservers 192.168.0.1


#auto br0
#iface br0 inet static
#       address 192.168.0.131
#       network 192.168.0.0
#       netmask 255.255.255.0
#       broadcast 192.168.0.255
#       gateway 192.168.0.1
#       bridge_ports p6p1
#       bridge_stp off
#       bridge_fd 0
#       bridge_maxwait 0
#

```

The commented out part at the bottom is the bridged interface I tried to create.

This is the output of ifconfig:
```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


p6p1      Link encap:Ethernet  HWaddr 50:e5:49:ed:e8:ec
          inet addr:192.168.0.130  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:feed:e8ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:36402 (36.4 KB)  TX bytes:66597 (66.5 KB)


virbr0    Link encap:Ethernet  HWaddr 42:af:6b:29:7d:a1
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I noticed that there is a 'virbr0' interface. I did not create that and it does not appear in /etc/network/interfaces

What is the problem here with the invoke-rc.d command?
Thanks for your help.

Manas

---

### Post by Manas B on 2014-06-26
I was making a mistake with the /etc/network/interfaces file, this is the updated version:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto p6p1
#iface p6p1 inet dhcp
iface p6p1 inet manual
#       address 192.168.0.130
#       netmask 255.255.255.0
#       gateway 192.168.0.1
#       broadcast 192.168.0.255
#       dns-nameservers 192.168.0.1


auto br0
iface br0 inet static
        address 192.168.0.130
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1
        bridge_ports p6p1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0


```

The invoke-rc.d command is still failing though.
```

> sudo invoke-rc.d networking restart
stop: Job failed while stopping
start: Job is already running: networking
invoke-rc.d: initscript networking, action "restart" failed

```

---

### Post by Tadaen_Sylvermane on 2014-06-26
service networking restart. Else just a reboot would do it.

---

### Post by Manas B on 2014-06-28
> **Tadaen_Sylvermane said:**
> service networking restart. Else just a reboot would do it.


Thanks.

---

