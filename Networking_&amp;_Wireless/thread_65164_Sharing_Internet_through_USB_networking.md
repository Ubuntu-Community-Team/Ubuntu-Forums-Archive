---
title: "Sharing Internet through USB networking"
date: 2005-09-13
forum: Networking &amp; Wireless
---

### Post by Navyblue on 2005-09-13
Hi All,

I am trying to access to internet from my iPaq 3870 (running Familiar Linux 0.82) through my PC (running Ubuntu Hoary). I have set up a USB network and I can ping each other with the Firestarter turned off (although I have set to allow the trafic from the iPaq's IP )

Btw, My PC is connected to a D-Link DSL-G604T wireless router through LAN cable. It has a built in ADSL modem. It saves the dialup information in it and all the PC would just need to connect to it by wired or wireless LAN to get to the internet.

Here are my IPs:

usb0 on my PC:

address 192.168.2.200
netmask 255.255.255.0
broadcast 192.168.2.255

iPaq
addressess 192.168.2.202
Subnet Mask 255.255.255.0
Gateway 192.168.2.200

I have installed "ipmasq" and "dnsmasq". Are these what I need? What should I do next so that the iPaq can have internet access?

Thanks. :)

---

### Post by Navyblue on 2005-09-13
In case these information would help:

/sbin/route

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 usb0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         mygateway       0.0.0.0         UG    0      0        0 eth0

```
/sbin/ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:0F:EA:79:8E:7F
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe79:8e7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:68884904 (65.6 MiB)  TX bytes:22253128 (21.2 MiB)
          Interrupt:22 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:252 (252.0 b)  TX bytes:252 (252.0 b)

usb0      Link encap:Ethernet  HWaddr C6:26:DE:E3:2C:94
          inet addr:192.168.2.200  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::c426:deff:fee3:2c94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:616 (616.0 b)  TX bytes:378 (378.0 b)

```

---

### Post by Navyblue on 2005-09-13
Btw again, I have done this and it still doesn't work.

sudo iptables -P FORWARD ACCEPT
sudo iptables -t nat -A POSTROUTING -s 192.168.2.202 -o usb0 -j MASQUERADE

Does it have anything t do with the gateway setting? If yes what should I do?

Thanks.

---

### Post by Navyblue on 2005-09-15
[QUOTE=Navyblue]Btw again, I have done this and it still doesn't work.

sudo iptables -P FORWARD ACCEPT
sudo iptables -t nat -A POSTROUTING -s 192.168.2.202 -o usb0 -j MASQUERADE

Does it have anything t do with the gateway setting? If yes what should I do?

Thanks.[/QUOTE]
 As usual, Pocket PC questions are unpopular here.

---

