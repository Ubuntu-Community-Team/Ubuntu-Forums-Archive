---
title: "Qualcom Atherlos QCA8171, no DNS resolution but other NIC works"
date: 2018-05-21
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2018-05-21
I have a new motherboard it has a Qualcom Atherlos QCA8171 gigabit Ethernet chip.

I have configured a static ip address in /etc/network/interfaces.

The on board NIC isn't working properly it almost works but the name service doesn't quite work.

When I boot from a DVD everything works like it should  

I installed a PCI network card using a Realtek RTL8169 chip and DNS started working. No idea why the onboard NIC didn't work. I have other machines using the same motherboard that work just fine and the only thing not working is DNS. Except for the name of the interface the configuration in /etc/network/interfaces is identical. 

nslookup works fine when specifying a name server, but not when not specifying one.
```
# nslookup www.google.com - 75.75.75.75
Server:         75.75.75.75
Address:        75.75.75.75#53

Non-authoritative answer:
Name:   www.google.com
Address: 216.58.195.68
```

I know I'm overlooking something simple but am drawing a blank.

```
# New Onboard Gigabit Adapter
auto enp1s0
iface enp1s0 inet static
address 192.168.1.24
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 75.75.75.75 75.75.76.76 8.8.8.8 8.8.4.4
```

```
ifconfig -a 
enp1s0    Link encap:Ethernet  HWaddr 70:85:c2:52:a7:90
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2603:3001:600:4a00:7285:c2ff:fe52:a790/64 Scope:Global
          inet6 addr: fe80::7285:c2ff:fe52:a790/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17344717 (17.3 MB)  TX bytes:24868460 (24.8 MB)
          Interrupt:19
```

From another post on a similar problem someone asked for this: 

```
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp1s0
```

Also I can ping an ip address just fine even one remote for our network.

I by editing the files in /etc/resolvconf/resolvconf.d and removing some incorrect information now 'nslookup' and 'host' work but ping still doesn work nor does apt update, it is unable to find the servers.

---

### Post by rsteinmetz70112 on 2018-05-24
I discovered one adapter was being manage by network manager and that was causing a conflict with /etc/network/interfaces. removed the configuration form /etc/network/interfaces and everything is fine. doing the configuration of that interface through network manager.

---

### Post by rsteinmetz70112 on 2018-05-26
I though I had the problem solved but it's not and has gotten more mysterious.

---

