---
title: "Confused by installation of new NIC"
date: 2015-01-20
forum: Networking &amp; Wireless
---

### Post by david.aldrich.ntml on 2015-01-20
Hi

I am running Ubuntu 10.04 on a newish Dell Optiplex desktop.  The machine has an onboard Ethernet controller, which I haven't used because it didn't work well with Ubuntu 10.04.  I need two Ethernet connections so I added two Intel Pro1000 NIC's to the PC.  The interfaces were labelled eth0 and eth1.  That worked fine.

For reasons I won't go into I had to remove one of the NICs for use in another system. I have now bought a new NIC and fiited it to the Optiplex.  But now I can't see eth1.

Here is what I do see:

```
-> lspci -vv | grep Ethernet
00:19.0 Ethernet controller: Intel Corporation Device 153a (rev 04)
01:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
03:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
```


So there appear to be 3 interfaces, as expected.

But I see eth2 instead of eth1:

```
-> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 68:05:ca:17:fd:4f  
          inet addr:172.29.68.54  Bcast:172.29.68.255  Mask:255.255.255.0
          inet6 addr: fe80::6a05:caff:fe17:fd4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28829 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:9229088 (9.2 MB)  TX bytes:1156673 (1.1 MB)
          Memory:f7dc0000-f7de0000 

eth2      Link encap:Ethernet  HWaddr 68:05:ca:2a:88:65  
          inet6 addr: fe80::6a05:caff:fe2a:8865/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:260604 (260.6 KB)  TX bytes:2178 (2.1 KB)
          Memory:f7cc0000-f7ce0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9624 (9.6 KB)  TX bytes:9624 (9.6 KB)
```

Trying to bring up eth1 does not work:

```
sudo ifup eth1
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
```

Finally here's my interfaces file:

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.111
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1:1
iface eth1:1 inet static
address 172.16.81.49
netmask 255.255.255.0

auto eth1:5
iface eth1:5 inet static
address 172.16.81.53
netmask 255.255.255.0
```

I need to see eth0 and eth1, not eth2. Please can anyone help me sort this out?

Best regards

David

---

### Post by kpatz on 2015-01-20
Edit the file  /etc/udev/rules.d/70-persistent-net.rules.  Remove the eth1 line and change eth2 to eth1.  Reboot.

---

### Post by david.aldrich.ntml on 2015-01-20
> **kpatz said:**
> Edit the file  /etc/udev/rules.d/70-persistent-net.rules.  Remove the eth1 line and change eth2 to eth1.  Reboot.

Thanks very much - that fixed the problem.

---

