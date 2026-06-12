---
title: "Server keeps dropping network connection, but VM machine is still connected."
date: 2013-11-29
forum: Networking &amp; Wireless
---

### Post by virtuosojoel on 2013-11-29
```
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise

```

I have a strange problem with my server. It keeps dropping off the local network, seemingly retaining its IP address, but dropping packets.
The odd thing is that the virtual machine running Windows 7 has no trouble connecting via the bridge from the same physical network port.

The temporary fix I've found is to use "ifdown eth0 && ifup eth0", which doesn't appear to disrupt the VM, and brings back the local network connection, although I'm still unable to ping the internet (8.8.8.8).
I did briefly get internet access after a reboot, so I downloaded updates, but the problem returned soon after.

It's an intermittent issue that happens 2-3 times a day, resetting eth0 will temporarily allow access to the local network.
I've tried using a static IP, since the IP address is reserved on the router, and DHCP as well. Both have the same result.

I am always able to access the Win7 VM remotely, and it has internet and local network access, except when it requires a reboot after using "service networking restart".

I've pasted the output from ifconfig below.

```

br0       Link encap:Ethernet  HWaddr 3c:4a:92:d5:67:73
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3e4a:92ff:fed5:6773/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:230630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15644601 (15.6 MB)  TX bytes:48307 (48.3 KB)

eth0      Link encap:Ethernet  HWaddr 3c:4a:92:d5:67:73
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3e4a:92ff:fed5:6773/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5133 errors:0 dropped:1129 overruns:0 frame:0
          TX packets:1015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1300335 (1.3 MB)  TX bytes:382441 (382.4 KB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:913817 (913.8 KB)  TX bytes:913817 (913.8 KB)

virbr0    Link encap:Ethernet  HWaddr 36:cc:09:8b:8b:30
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:1d:cb:fa
          inet6 addr: fe80::fc54:ff:fe1d:cbfa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:5380145 (5.3 MB)  TX bytes:28211190 (28.2 MB)

```

*Edit:*

I ran 5000 pings on the VM. The server dropped 200 packets during that time, but the VM had 0% packet loss.

---

