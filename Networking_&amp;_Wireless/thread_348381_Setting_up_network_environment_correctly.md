---
title: "Setting up network environment correctly"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by lilalfyalien on 2007-01-28
Hi,

This perhaps is a very simple question, with a very simple answer, or so I'm hoping. I'm trying to run a java program which works perfectly on windows xp, however when I run it on my ubuntu machine it comes back with a broken pipe error. This I'm told by java whizzes is a networking error within my own computer's setup. I've traced this a bit further and it looks like my code is trying to find out my IP address from ubuntu, but is either not getting it or getting it in a format which it doesn't recognise. Would ubuntu not "give" java this information for any reason? Permission problems for example?

I'm wondering whether I've setup my IP address right on my computer. I've been into System>Administration>Networking and my computer is currently known as the following hosts:

```
fe00::0
ff02::1
::1
127.0.0.1
10.0.0.26
ff02::3
ff00::0
ff02::2
```

ifconfig -a -v reveals:
```

eth0      Link encap:Ethernet  HWaddr 00:02:B3:08:A5:3A
          inet addr:10.0.0.26  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fe08:a53a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:77252577 (73.6 MiB)  TX bytes:4541166 (4.3 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46025 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11602697 (11.0 MiB)  TX bytes:11602697 (11.0 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0

```

Does this configuration look healthy? Can I delete any entries? Is there any other way that ubuntu might return my Ip, which might through java off (ie alpha, or alphanumeric characters as java complains that it can't convert what it's getting back into numbers- which would imply that they are either strings or nothing). How can I specify what it returns via ubuntu (as I'm using third-party code which is the code that's dying)?

If anyone has any ideas as to why my java program cannot get hold of the computer's IP address please let me know- any suggestions at all-because this problem is so frustrating.

Please help me!

Many thanks,

Lilalfyalien

---

### Post by scoon on 2007-01-28
Hey there,

Are you running a firewall that would block programs fro getting that info?

-scoon

---

### Post by lilalfyalien on 2007-01-29
Thanks for the reply.

I haven't set one up because I have a built in firewall in my router/gateway, not the computer. It wouldn't go out to that and then come back in would it? I can only do port forwarding on that...

Are there any other reasons that Java might not get hold on my IP address?

---

### Post by lilalfyalien on 2007-01-29
Does my setup seem healthy?

---

### Post by scoon on 2007-01-29
Hey there, 

Assuming this is a terminal app, try increasing the verbosity that you currently use.  Short of seeing your code, there doesn't seem to be anything that jumps out as problematic.

-scoon

---

### Post by dbott67 on 2007-01-29
These commands will reveal most of the information required:

This command outputs the network hardware detected:

```
sudo lshw -C network
```

Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

This command shows the contents of your interfaces file & whether they are automatically enabled, are using DHCP or static, etc.

```
cat /etc/network/interfaces 
```

Here's mine as an example:

```
dbott@dapper:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```


This command tries to detect wireless access points using each NIC:

```
iwlist scanning
```

```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

This command prints out your routing table:

```
route -n
```

```
dbott@dapper:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

For firewall information, type:
```
dbott@thedrake:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

-Dave

---

