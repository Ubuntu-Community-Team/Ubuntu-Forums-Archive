---
title: "RX packets errors only on port forward Ethernet."
date: 2016-06-01
forum: Networking &amp; Wireless
---

### Post by Raymond Day on 2016-06-01
Just don't get why this is. I got Ubuntu 16.04 server and have two USB to Gigabit Ethernet. I have one port foreword so I can get to it on the web. But it gets RX packets dropped errors. It does seem to work good but the errors add up and I like to fix this. I never seen it on a 10/100 but on the 1000 I see it and I switch a lot of Gigabit Ethernet cables and it don't fix it.

Because I have 2 Gigabit ports. I can edit the /etc/networks/interfaces file and switch then. So the port foreword one is the static and the other one to dynamic. Were it auto gets a IP. When ether one is is dynamic they don't get errors but when I just switch them in the interfaces file then the one I have static starts to get errors.

I guess it's some setting I my have not sure.

It's the same hardware when I switch it so that can't be it. I guess it's some setting I have.

Here is what my interfaces file looks like now if this helps:

```
# interfaces(5) file used by ifup(8) and ifdown(8)

#J5 Create USB-C hub = enx0050b619c659
#Ableconn USB-C hub = enx00051ba6b8ff

auto lo enx00051ba6b8ff enx0050b619c659
iface lo inet loopback

#iface enx00051ba6b8ff inet static
iface enx0050b619c659 inet static
	address 192.168.2.109
	netmask 255.255.255.0
	broadcast 192.168.2.255
	network 192.168.2.0
	gateway 192.168.2.1
	dns-nameservers 127.0.1.1 8.8.8.8 8.8.4.4
	dns-domain hsd1.mi.comcast.net
```

It's something it don't get errors when one or the other is on dynamic but one or the other both get errors when on a Static IP.

-Raymond Day

---

### Post by SeijiSensei on 2016-06-01
Are they both on the same IP subnet,  192.168.2.0/24?  That can cause all sorts of problems.

---

### Post by Raymond Day on 2016-06-01
I am not sure what a subnet is or how to set it. All my things are on the same 192.168.2.* 1 to 255 I think.

This my help my ifconfig command shows this:

```
enx00051ba6b8ff Link encap:Ethernet  HWaddr 00:05:1b:a6:b8:ff
          inet addr:192.168.2.220  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::35a5:1372:6734:8565/64 Scope:Link
          inet6 addr: 2601:40d:4480:456:df77:eb6a:8c39:7037/64 Scope:Global
          inet6 addr: 2601:40d:4480:456:24b1:7bd5:3552:5042/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:277304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:50473730 (50.4 MB)  TX bytes:1442722 (1.4 MB)

enx0050b619c659 Link encap:Ethernet  HWaddr 00:50:b6:19:c6:59
          inet addr:192.168.2.109  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:b6ff:fe19:c659/64 Scope:Link
          inet6 addr: 2601:40d:4480:456:f18b:98a4:6357:c716/64 Scope:Global
          inet6 addr: 2601:40d:4480:456:250:b6ff:fe19:c659/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20019456 errors:0 dropped:219 overruns:0 frame:0
          TX packets:14956811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19036502902 (19.0 GB)  TX bytes:16090256042 (16.0 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:345604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:345604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:113108055 (113.1 MB)  TX bytes:113108055 (113.1 MB)

wlp2s0    Link encap:Ethernet  HWaddr a4:34:d9:0d:c7:df
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::4187:51bc:c793:7fab/64 Scope:Link
          inet6 addr: 2601:40d:4480:456:cae7:21ab:617c:b825/64 Scope:Global
          inet6 addr: 2601:40d:4480:456:954c:1552:b352:95c9/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25852654 (25.8 MB)  TX bytes:1044311 (1.0 MB)
```

If that helps. You can see how RX dropped 219 that is what I want to fix.

-Raymond Day

It's fixed! All I had to do it unplug the other Ethernet interface! It's been a few hours and it's not getting errors now.

Found out in the /etc/network/inerfaces file have to put the name of the Ethernet like this:

auto lo enx0050b619c659

if you just have it like this:

auto lo

It will not bring it up on boot up.

-Raymond Day

Looks like it's not fixed. It was up about 8 hours no errors. It has some updates to do and I did them and it had to reboot. After I rebooted it's starting to get errors again!

Don't get why that would be?

-Raymond Day

---

