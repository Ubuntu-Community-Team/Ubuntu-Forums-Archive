---
title: "Feisty. NetworkManager and a confused Red Hat user"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by worldofnic on 2007-04-11
I come from a Red Hat/Fedora background. I am confused by the interaction between NetworkManager and [FONT="Courier New"]/etc/network/interfaces[/FONT].

My (Dell) laptop has a builtin ipw3945 wireless card (eth1). But it doesn't come up at boot time (is it meant to?) or when I log in. I'm only using WEP.

Here's my [FONT="Courier New"]/etc/network/interfaces[/FONT] :

```
auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.2.25
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid nic-home3
wireless-key REMOVED! :-)

auto eth1

#iface eth0 inet dhcp

#auto eth0
```

If I run the following by hand after I log in, then all is fine. So what am I missing from the network configuration? What other files need changing?


```
sudo ifconfig eth1 inet 192.168.2.25
sudo iwconfig eth1 essid nic-home3
sudo route add -net default gw 192.168.2.1
```

---

### Post by spd106 on 2007-04-11
I think we're all still a bit confused with this in Feisty. I think the current procedure is to ensure that you have disabled roaming mode, then use network-admin.

As long as roaming mode is off, you should be ok to use the cli as well, how dhcp is supposed to fit in... I have no idea.

Instead of those three commands you should be able to run this command
```
sudo ifup eth1
```

---

