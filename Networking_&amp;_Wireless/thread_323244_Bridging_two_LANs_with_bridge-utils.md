---
title: "Bridging two LANs with bridge-utils"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by Steve Smith on 2006-12-21
I'm following [instructions on the wiki](https://help.ubuntu.com/community/BridgingNetworkInterfaces) to set up a bridge.

eth0 has a windows machine (DHCP server) at 192.168.0.1
eth1 has a windows machine (client of Ubuntu DHCP server) currently at 192.168.1.199

192.168.0.1 has to remain a DHCP server as the internet comes in through it on Windows internet connection sharing.

Before setting up the bridge, the ubuntu machine can ping either win machine.  Here is my /etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static

# LTSP network interface
auto eth1
iface eth1 inet static
        address 192.168.1.254
        netmask 255.255.255.0

# Bridge between this server's two network interfaces
auto br0
iface br0 inet static
       bridge_ports eth0 eth1
       address 192.168.0.253
       netmask 255.255.0.0

```

I've tried iface br0 inet dhcp and it didn't work.  With the static settings you can ping 192.168.0.1 but not 192.168.1.199.  If I change the bridge to 192.168.1.253 obviously that reverses.

Should I be able to have br0 on DHCP, and either way, an ideas why it doesn't work? :)

---

### Post by Rippey on 2006-12-21
looks to me like your problem can be solved with routing, not bridging.
try deleting the bridge and  type this in the console.

route add -net 192.168.1.0 netmask 255.255.255.0 dev eth1
route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0

this should work if I understand your problem corectly.

if not, post some more details about your networksetup.

---

### Post by Steve Smith on 2006-12-22
Thanks, but that didn't appear to do anything!  Has that been written to a text file somewhere, that I should remove it from before I try anything else?

I've attached a diagram of my network.  I'm trying to make 'steve' and 'duron' be able to ping each other, with the hope that I can then have internet access on 'steve'.

---

### Post by Rippey on 2006-12-22
when you type route in the console it should look like this now

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.68.1.0      *               255.255.255.0   U     0      0        0 eth1
192.68.0.0        *               255.255.255.0   U     0      0        0 eth0
default         192.68.0.1        0.0.0.0         UG    0      0        0 eth0

2 things that could still be wrong if you get the above output on blackbox:
1. steve should have blackbox as defaultgateway
2. duron should know that it has to route all trafic for 192.68.1.0 to blackbox

hope this helps.

---

### Post by Steve Smith on 2006-12-23
I'll try that later!  One question:

> **Rippey said:**
> duron should know that it has to route all trafic for 192.68.1.0 to blackbox

How do you do that on Windows?!

---

### Post by Rippey on 2006-12-23
on duron open the command promt (start>run>cmd) and type: 

route -p add 192.168.1.0 mask 255.255.255.0 192.168.0.0

if that doesn't work you could try to give blackbox a static ip and change the last ip in the command to the static ip you've given blackbox.

more on routing in windows can be found [here]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/route.mspx").

---

### Post by Steve Smith on 2007-01-25
I'm finally back onto getting the server working now!

LTSP's stopped working, and I think it's to do with the routing I've tried to set up here.  How do I remove the results of

```

route add -net 192.168.1.0 netmask 255.255.255.0 dev eth1
route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0

```

Is it in a config file somewhere?

---

### Post by Paris Heng on 2007-08-15
> **Steve Smith said:**
> I'm finally back onto getting the server working now!

LTSP's stopped working, and I think it's to do with the routing I've tried to set up here.  How do I remove the results of

```

route **add** -net 192.168.1.0 netmask 255.255.255.0 dev eth1
route **add** -net 192.168.0.0 netmask 255.255.255.0 dev eth0

```

Is it in a config file somewhere?


Just replace the **add** with **del**:

```

route **del** -net 192.168.1.0 netmask 255.255.255.0 dev eth1
route **del** -net 192.168.0.0 netmask 255.255.255.0 dev eth0

```

**route -n ** to check weather the route is deleted.

Source: [http://linux.about.com/od/commands/l/blcmdl8_route.htm](http://linux.about.com/od/commands/l/blcmdl8_route.htm)

---

