---
title: "What is the difference (networking)"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by OOzypal on 2007-04-05
I need to setup my wireless card. I got confused about these IPs. What is the difference between address, gateway, netmask, network, broadcast, etc.

Sorry, I know is easy question but I could find an answer for in google.

auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255

---

### Post by spd106 on 2007-04-05
Address - The "name" other computers use to talk to you (must have).

Netmask - Complicated, but you probably won't need anything other than 255.255.255.0 (must have)

Gateway - The address of the next hop to the internet, usually your router. I has to be on the same network as your computer or you won't be able to reach it (must have, if you want an Internet connection).

Broadcast - The address used to talk to all other computers on the network (not necessary).

Network - Usually the first address on a network subnet (not necessary).

The last two are calculated from the address and netmask, so they aren't necessary unless you have a special setup. If you do, then contact your network admin for help. 

The order is significant, look in *man interfaces* for more details.

---

### Post by OOzypal on 2007-04-05
GR8

Now, I need to setup my wireless router (ADSL). My Kubuntu can find two cards

eth0 (Ethernet) and eth1 (Wireless)

I need to disable eth0 and keep eth1 up and running for wireless. How can I do this? Do I actually need to disable eth0 to work with eth1?

BTW, no mater what I do in /etc/network/interfaces when I go to K Menu>>System Settings >> Network Settings I see different parameters and IP addresses. If I disable eth0 from there and restart the computer, the eth0 is enabled again.

Here is my /etc/network/interfaces file content

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

ifdown eth0

auto eth1
iface eth1 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
wireless-essid BNet
wireless-key 17E9A39451

```

---

### Post by spd106 on 2007-04-05
Try adding an eth0 stanza but just omit the auto line.
i.e.
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
wireless-essid BNet
wireless-key 17E9A39451

```

I'm not familiar with KDE, but this should work.

---

