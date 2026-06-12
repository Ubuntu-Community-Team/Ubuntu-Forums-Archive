---
title: "I plug the ethernet cable to a new ethernet card but there is not internet."
date: 2014-05-17
forum: Networking &amp; Wireless
---

### Post by feesgo on 2014-05-17
I use Ubuntu 12.04

I have a onboard ethernet card. That ethernet card does not work anymore.

I have installed another ethernet card in a pci slot

I plug the ethernet cable to the new ethernet card but there is not internet.

When i run ifconfig it shows:


eth0      Link encap:Ethernet  HWaddr 00:1c:c0:74:d2:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:e3100000-e3120000 

eth2      Link encap:Ethernet  HWaddr c0:4a:00:01:12:65  
          inet6 addr: fe80::c24a:ff:fe01:1265/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22165684 (22.1 MB)  TX bytes:2849991 (2.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4048 (4.0 KB)  TX bytes:4048 (4.0 KB)


When I open "System Settings / Network" appear two WIRED connections buth both show the legend "Cable unplugged"

I have internet when i run the command:

sudo dhclient eth2

After this command I run ifconfig and it shows:

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:74:d2:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:e3100000-e3120000 

eth2      Link encap:Ethernet  HWaddr c0:4a:00:01:12:65  
          inet addr:192.178.0.6  Bcast:192.178.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c24a:ff:fe01:1265/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22180384 (22.1 MB)  TX bytes:2855977 (2.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4048 (4.0 KB)  TX bytes:4048 (4.0 KB)



How can I avoid to run "sudo dhclient eth2" every time I turn on my machine?

---

### Post by Bashing-om on 2014-05-17
feesgo; Hi !

Check the file " /etc/network/interfaces "
I bet changing 'eth0' to 'eth2' will go a long way to resolving the issue:
as in:
```

    # The primary network interface
##changed eth0 to eth1 26feb2014##
auto eth1
iface eth1 inet dhcp

```
To continue to have the "network managed" with eth2 as the default connection.

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

