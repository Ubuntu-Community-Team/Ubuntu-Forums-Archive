---
title: "Internet wont work while bridging"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by jrodri14 on 2008-06-16
I'm setting up multiple vm's and I've set up their bridging, which works well (Took a while to figure that out). But I lose internet connectivity on the host whenever my bridge interface (br0) is active. I have to remove the br0 interface from the interfaces and restart in order to have access to the internet. But then my vm's dont have any access.

Can someone help plz.

---

### Post by SpaceTeddy on 2008-06-16
what your setup ? can you post all /etc/network/interfaces as well as all output from route -n.

hope we can figure this out :)

---

### Post by jrodri14 on 2008-06-16
this is my 'route -n'

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 br0
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br0
0.0.0.0         10.0.1.1        0.0.0.0         UG    100    0        0 eth1
0.0.0.0         10.0.1.1        0.0.0.0         UG    100    0        0 br0

and my 'interfaces'


auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
#       address 10.0.1.34
#       netmask 255.255.255.0
#       broadcast 10.0.1.250
#       gateway 10.0.1.35
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

#iface eth0 inet dhcp

#auto eth0

iface eth1 inet dhcp

auto eth1


The router is on 10.0.1.1

Whenever I ping google, I dont get farther than the router

Thx a lot.

---

### Post by SpaceTeddy on 2008-06-16
> **jrodri14 said:**
> this is my 'route -n'

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 br0
**10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1**
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br0
**0.0.0.0         10.0.1.1        0.0.0.0         UG    100    0        0 eth1**
0.0.0.0         10.0.1.1        0.0.0.0         UG    100    0        0 br0

the bold line should be the problem. Since eth0 is bridged, it should NOT have any ipconfiguration - only br0 should be configured. This overwrites your standard gateway rendering your connection to the internet useless (or so i see it)
> **jrodri14 said:**
> 
auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
#       address 10.0.1.34
#       netmask 255.255.255.0
#       broadcast 10.0.1.250
#       gateway 10.0.1.35
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

#iface eth0 inet dhcp

#auto eth0

**iface eth1 inet dhcp**

auto eth1

remove the bold line - you do NOT want eth0 to do anything but come up. plain existance of the interface is enough. Although, what you want to do is make sure that eth0 is in promisc mode, so that it reads any and all pakets coming in and passing it on to br0. to do that, add the following lines to the /etc/network/interfaces:

```
auto eth1
iface eth1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down 
```

DO NOT replace the $IFACE !

that should fix the problem... i hope :)

PS: the bridge configuration is taken from this [[COLOR="Blue"]tutorial[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127"), part 2, chapter 3.

---

### Post by jrodri14 on 2008-06-16
but why eth0? Its a second adapter on my mb that I dont use... or do you mean eth1?

---

### Post by SpaceTeddy on 2008-06-16
ups, typo... yes, i mean eth1 - sorry :)

---

### Post by jrodri14 on 2008-06-16
Wow, thanks; it worked. I would have never figured that out! Could you please explain what that does?

---

### Post by SpaceTeddy on 2008-06-16
i don't have much time to explain this (as it is late and i need sleep) - but i'll try to wrap this as simple possible. 

First thing is understanding how the bridging works. You create a new network card (in your case br0) which you then can stuff network card into (like your eth1 and your tun device). Since the br0 is a container, it will handle everything that comes in on ALL network cards that are part of it. 
If you now add a configuration to the bridge as well as a device IN the bridge, you get a double configuration on the same device. So, essentially, you have two different network devices (for linux) with the same ip-address and the same default gateway. Since ip-configuration need to be unique, the kernel could not decide anymore which interface to use (although they are the same - but the kernel cannot see that !!!). So it got stuck and your internet did not work anymore. 

What i did is take out the dhcp configuration of the physical device and only left the bridge to handle everything. But for that to work, you need the physical mode in promiscuous (called promisc) mode - meaning it will accept any and all packet and hand it down to the br0 device. Otherwise, the physical network card would only accept packets within it's own ip-segment - which it does not have anymore. So, we need to send eth1 into that mode WITHOUT it obtaining an ip address. Also, we need eth1 to be up - if it is down, it is useless. And that is exactly what these commands to. I'll quickly walk through them

```
auto eth1
```
this tells the kernel to load the device upon boot
```
iface eth1 inet manual
```
this tells the kernel that this interface will be configured manually. There is not ip and no dhcp for it - we want it just to be there. 
```
up ifconfig $IFACE 0.0.0.0 up
```
the **up** means that if the interface comes up, this command should be run. the $IFACE in there will be replaced by eth1. But to be generic, i just left it like that, as this will work with any network device. So the command that runs really is **ifconfig eth1 0.0.0.0 up** which again brings the interface up and configured it to have NO IP.
```
up ip link set $IFACE promisc on
```
This works the same was the command before, so it will actually run **ip link set eth1 promisc on** which will enable the promisc mode on the interface. So now we are done. We have an interface that is up, unconfigured and in promisc mode. 

```
down ip link set $IFACE promisc off
down ifconfig $IFACE down
```
this does the same as the two up commands, they are just ran when the interface is going down. So this unconfigured the network card.

hope this is understandable :)

---

### Post by jrodri14 on 2008-06-16
Wow. Now it all makes sense. THX A LOT. :)

---

