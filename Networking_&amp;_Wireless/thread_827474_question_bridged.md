---
title: "question bridged"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by joeboentoe on 2008-06-12
/etc/network/interfaces config
auto lo
iface lo inet loopback

auto eth0 tap1 br0

iface eth0 inet manual

iface tap1 inet manual
    sudo /usr/sbin/tunctl -t tap1 -u userme

iface br0 inet dhcp 
  bridge_ports eth0 tap1
  pre-up ip link set eth0 promisc on


I am using virtualbox bridged settings. I attached tap1 to the network adapter of the virtual machine. Everything works fine.

But if I execute ipconfig in the virtual machine which is win xp then I see an ipaddress. If I execute ifconfig on the host(ubuntu) then I get the four devices, and only br0 gets an ip. Why doesn't eth0 gets an ip? I thought eth0 was my physical network adapter, so how does it know what source ip to use when it sends a packet. What if I had 2 physical network adapters under one bridge? How do u assign an ip for each of them?

thanks

---

### Post by joeboentoe on 2008-06-18
SOLVED

It is just a switch. So it operates on layer 2. In my case it's a switch with 2 ports I think.

---

