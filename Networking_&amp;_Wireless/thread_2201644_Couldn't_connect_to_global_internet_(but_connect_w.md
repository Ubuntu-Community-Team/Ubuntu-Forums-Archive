---
title: "Couldn't connect to global internet (but connect well in local network)"
date: 2014-01-25
forum: Networking &amp; Wireless
---

### Post by maglev on 2014-01-25
Hi everyone,

I recently installed ubuntu 12.04 to my PC.
I use the PC as a local server.
(I only need to access it from local network)

For internet connection,
I am using mobile wireless router which also work as local network.

Here's the problem happened recently.

Other devices in my local network can access the computer without any problem.
The computer could also access local network, but cannot access internet.
Restarting network several times rarely solve the problem,
but the problem is ocurred each time I reboot the PC.

Basically I can access internet if I use wired connection,
but not with the wireless one.
For wireless connection, I use USB wifi device.

Here's output of lspci:
```
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation Panther Point KT Controller (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 104a (rev a1)
01:00.1 Audio device: NVIDIA Corporation HDMI Audio stub (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 Multimedia controller: Altera Corporation Device 4c15 (rev 01)

```

How could I connect to internet with wireless device?
Is anything wrong with my configuration?

I am in 12.04 64bit, 8 GB memory,
Intel Core i3-3220T.

I already searching around, but couldnt find a good solution.

Really appreciate any help. Thanks.

---

### Post by Iowan on 2014-01-25
You can check **route -n** to see which interface is *supposed* to be used.
**ifconfig** might show if both interfaces are in the same subnet.

---

### Post by maglev on 2014-01-25
Thanks for your reply, Iowan.

Here's is **route -n** output:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```
above output is exactly same to other PC's output,
which connect to internet well.

I am not an expert in linux,
and have been looking around to understand the routing commands,
but couldn't find any problem in the setting.

Here's **ifconfig** output:
```
eth0      Link encap:Ethernet  HWaddr d4:3d:7e:d8:2a:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:30500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2069832 (2.0 MB)  TX bytes:2069832 (2.0 MB)

wlan0     Link encap:Ethernet  HWaddr 00:22:cf:b8:96:6c  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:cfff:feb8:966c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22597732 (22.5 MB)  TX bytes:876415 (876.4 KB)

```

---

### Post by steeldriver on 2014-01-26
Is this a server (no GUI) or desktop? are you using the GUI network-manager or CLI /etc/network/interfaces file?

What exactly do you mean by "cannot access internet"? can you

[LIST]
[*]not ping external hosts even by IP 
[*]ping external hosts by IP but not by name 
[*]ping by IP and name but the pages don't load 
[/LIST]

---

### Post by maglev on 2014-01-26
Thanks for your response.

It's a desktop.
I am using the GUI network-manager to configure the network.

"cannot access internet" means I can

[LIST]
[*]not ping external hosts even by IP
[/LIST]

Thank you in advance.

---

### Post by Iowan on 2014-01-26
Can you **ping** the router?

---

### Post by maglev on 2014-01-26
Yes I can ping the router perfectly.

```
> ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=255 time=1.25 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=255 time=1.28 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=255 time=1.53 ms
64 bytes from 192.168.0.1: icmp_req=4 ttl=255 time=1.78 ms
64 bytes from 192.168.0.1: icmp_req=5 ttl=255 time=1.30 ms
64 bytes from 192.168.0.1: icmp_req=6 ttl=255 time=1.53 ms
64 bytes from 192.168.0.1: icmp_req=7 ttl=255 time=4.94 ms
64 bytes from 192.168.0.1: icmp_req=8 ttl=255 time=1.36 ms
64 bytes from 192.168.0.1: icmp_req=9 ttl=255 time=1.28 ms


```

---

### Post by steeldriver on 2014-01-26
Is there any kind of access control set up on the router that might be disallowing access based on the wireless MAC? what does

```
mtr google.com
```

say? can it see past the router at all?

---

### Post by Iowan on 2014-01-26
What messages do you get when you try to **ping** external hosts?

---

### Post by maglev on 2014-01-26
mtr google.com results :
```
Failed to resolve host: Name or service not known.
```

I reset the router to factory settings recently (after this problem),
and other PC/devices connected to the router could connect to internet,
so I think it is not a router settings problem.

When I try to ping external host by name:
```
ping: unknown host ping
```and by IP:
```
PING 216.239.51.99 (216.239.51.99) 56(84) bytes of data.

(no following response even after several minutes)

```

---

### Post by steeldriver on 2014-01-26
I am not able to ping 216.239.51.99 either so it's not a good test - try pinging one of the google DNS servers instead

```
ping 8.8.8.8
```

---

### Post by maglev on 2014-01-26
Some sites say that 216.239.51.99 is google's IP so I used it :D
But seems that it is not a good example for ping.

I ping 8.8.8.8 and success.
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=48 time=137 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=48 time=137 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=48 time=219 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=48 time=138 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=48 time=137 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=48 time=136 ms
```

So I correct my statement on previous post:
I can:

[LIST]
[*]ping external hosts by IP but not by name 
[/LIST]

---

### Post by steeldriver on 2014-01-26
OK so it is likely a name resolution issue. Since it works when you are connected via wired ethernet, it's unlikely to be anything fundamental about your setup, perhaps you have just configured the wireless network differently (e.g. to use manual DNS servers rather than obtaining them via DHCP) - I suggest opening up the connection editor either from the GUI indicator panel or from a terminal by typing

```
nm-connection-editor
```

and then look carefully at the 'IPv4 Settings' tab of both the wired and wireless connection to see what's different

---

### Post by maglev on 2014-01-26
I found one difference on their settings:

On wlan "IPv4 settings", the "DNS server" was empty,
so I put my router address there (192.168.0.1)

I restart the network, and BINGO!
It works!

Thank you very much man!
You made my day!

---

