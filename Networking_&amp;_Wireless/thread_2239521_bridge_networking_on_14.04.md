---
title: "bridge networking on 14.04"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by x-terry on 2014-08-14
I have installed ubuntu 14.04 as a clean install (deleting 12.04).

I tried copying the network interfaces file which was working fine on 12.04. The file is as follows:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
address 192.168.1.100
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
bridge_ports eth0
bridge_fd 0
bridge_maxwait 0
bridge_stp off

On reboot the network did not start, so I edited the file for a standard static network:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
#iface eth0 inet manual

#auto br0
#iface br0 inet static
address 192.168.1.100
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
#bridge_ports eth0
#bridge_fd 0
#bridge_maxwait 0
#bridge_stp off

This works fine. Can anyone suggest why my bridged setup didn't work?
FYI ifconfig shows the following:

eth0      Link encap:Ethernet  HWaddr bc:ee:7b:5f:8b:f7  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beee:7bff:fe5f:8bf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39315 (39.3 KB)  TX bytes:14539 (14.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13230 (13.2 KB)  TX bytes:13230 (13.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.159.1  Bcast:172.16.159.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.34.1  Bcast:192.168.34.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Thanks,

Terry

---

### Post by TheFu on 2014-08-14
I use something like this:
```

# ####################################
auto br0
iface br0 inet static
  address 172.22.22.6
  gateway 172.22.22.1
  netmask 255.255.255.0
  broadcast 172.22.22.255
  # mtu 9014
  dns-nameservers 172.22.22.1
  dns-search example.com example.lan
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off
```

---

### Post by x-terry on 2014-08-15
Thanks for your response. It seems that I no longer need to use bridge networking. I originally used KVM for my virtual server, which required it to allow the guests to be available on the LAN. it seems that vmware creates its own virtual network and so my original config is no longer required.

---

