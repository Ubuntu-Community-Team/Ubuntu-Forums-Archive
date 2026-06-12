---
title: "2 Network Adapters in Ubuntu VirtualBox Guest, but no Internet connectivity"
date: 2016-11-28
forum: Networking &amp; Wireless
---

### Post by orionsg on 2016-11-28
I have a setup with two network adapters on an Ubuntu 16.04 VirtualBox guest with:

Network Adapter 1: Bridged network connection (supposed to give the internet connection)
Network Adapter 2: Host-only network whereby I have connection to the host and other VirtualBox guests

I have tried with various configuration of the /etc/network/interfaces file. Best result is when I just leave it at its basic configuration:
```

auto lo
iface lo inet loopback

```

Thus the specific network properties are setup using "Network" under "System Settings", i.e. the Unity desktop and not in the interfaces file.

ifconfig gives:
```

enp0s3    Link encap:Ethernet  HWaddr 08:00:27:25:4d:38  
          inet addr:192.168.0.114  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::fdce:a4b4:629d:49dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:363509 (363.5 KB)  TX bytes:12161 (12.1 KB)

enp0s8    Link encap:Ethernet  HWaddr 08:00:27:4f:3b:3e  
          inet addr:192.168.56.3  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::4966:9091:412d:7a24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35766 (35.7 KB)  TX bytes:9055 (9.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:9077 (9.0 KB)  TX bytes:9077 (9.0 KB)

```

For network 1 (enp0s3), the address is assigned automatically by DHCP.
For network 2 (enp0s8), the address is static:

I can ping to and from the guest using both networks so they are apparently both active. However, there is no Internet connectivity, which is the big issue.

If I deactivate network connection enp0s8 (using Unity network function), I immediately gain Internet connectivity though enp0s3. So there must be a conflict of some kind.

I will appreciate any help as I need both the host-only network and the internet connection to be active.

---

### Post by SeijiSensei on 2016-11-28
Did you enable packet forwarding by uncommenting the line "net.ipv4.ip_forward=1" in /etc/sysctl.conf?  If not, do that and reboot.  Any better?

---

### Post by orionsg on 2016-11-28
I have uncommented the line [COLOR=#000000]"net.ipv4.ip_forward=1" in /etc/sysctl.conf[/COLOR] and rebooted. 
Unfortunately, there is still no internet connection.

---

### Post by SeijiSensei on 2016-11-29
How about masquerading?  Do you have an iptables rule like
```
/sbin/iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
```
assuming enp0s3 is the Internet-facing interface.

If that doesn't work try
```
/sbin/iptables -t nat -A POSTROUTING -o enp0s3 -j SNAT --to 192.168.0.114
```

---

### Post by orionsg on 2016-12-01
I tried the two iptable commands. Unfortunately, there is still no internet connection.

As mentioned earlier, once I deactivate enps08 using Settings->Network in Unity, the internet connection through enps03 works right away. So something must be conflicting somehow.

---

