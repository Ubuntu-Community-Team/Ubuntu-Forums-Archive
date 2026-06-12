---
title: "2 IP on same network interface"
date: 2005-07-11
forum: Networking &amp; Wireless
---

### Post by shocy on 2005-07-11
Hi,

I'm looking over a server with Ubuntu and I have a small problem. 

I want to assign 2 IP's on the same network interface. I already did that through ifconfig. The problem is that I need the second IP to be configured at boot time in the /etc/network/interfaces file. The thing is that I added it but I'm not sure if it's correct and I don't want any problems the next time the server reboots. 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 172.16.10.91
        netmask 255.255.0.0
        network 172.16.0.0
        broadcast 172.16.255.255
        gateway 172.16.10.80
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 130.186.1.53

iface eth0:1 inet static
    address 10.0.0.23
    netmask 255.255.255.0
    gateway 10.0.0.1


auto eth0



```


Maybe someone can look over my config file and suggest corrections if needed.

---

### Post by sksbir on 2005-07-11
I suggest you to add
auto eth0:1
if you want it to start at boot.

---

