---
title: "Bridge Interface W/ VirtualBox Not Working"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by SupaRice on 2008-06-24
So I've got Ubuntu 8.04, and I installed the latest version of VirtualBox via the .deb from the site.  I then followed the directions in the VirtualBox user manual for setting up a bridge interface and assigning a vbox0 to it.  My WindowsXP guest networking doesn't seem to work though.  I've combed through some of the threads and can't figure out what I've got wrong.

I did:
```

sudo apt-get install bridge-utils
sudo VBoxAddIF vbox0 <user> br0
chmod 666 /dev/net/tun

```

And my ifconfig:
```

br0       Link encap:Ethernet  HWaddr 00:1d:09:9c:8a:bd  
          inet addr:172.20.227.210  Bcast:172.20.227.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe9c:8abd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7205789 (6.8 MB)  TX bytes:1290801 (1.2 MB)

eth0      Link encap:Ethernet  HWaddr 00:1d:09:9c:8a:bd  
          inet6 addr: fe80::21d:9ff:fe9c:8abd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1045924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:549302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1555093968 (1.4 GB)  TX bytes:40731369 (38.8 MB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130742 (127.6 KB)  TX bytes:130742 (127.6 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:de:c5:08:d4  
          inet6 addr: fe80::2ff:deff:fec5:8d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:31 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:22009 (21.4 KB)  TX bytes:17184 (16.7 KB)

```

And my /etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 172.20.227.210
        netmask 255.255.255.0
        network 172.20.227.0
        broadcast 172.20.227.255
        gateway 172.20.227.1
        dns-nameservers 172.20.227.209
        dns-search here.com
        bridge_ports eth0

```

After a while it seems that I end up with connectivity issues on the host when eth0 takes it upon himself to obtain a DHCP address, and I have the static still assigned to br0.

I also entered "host interface" under attached to in the network settings, and entered "vbox0" under "interface name".

I'm sure this is something simple and dumb, anyone know what I've done wrong?

Arrghh!

Thanks in advance for any help.

---

### Post by SupaRice on 2008-06-25
Anyone?.... Anyone?.... Bueller?

---

