---
title: "Ubuntu Server VM required to run dhclient every startup"
date: 2014-03-21
forum: Networking &amp; Wireless
---

### Post by vince8 on 2014-03-21
Hi,

I set up an Ubuntu Server VM (12.04 LTS) via VirtualBox the other day, and if I try to give it a static IP on my network, I'm required to run dhclient every time I want to connect to the internet.  I'm using a bridged connection and, the weirdest part, is that I set up a very similar VM about 8 months ago that does not experience this issue.

Here are the contents of /etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.11.8
        netmask 255.255.255.0
        network 192.168.11.0
        broadcast 192.168.11.255
        gateway 192.168.11.1

If I uncomment the dhcp line and comment out the inet static configuration, it works fine, but then I no longer have the static IP.  Any thoughts on what could be causing this issue?

Please let me know if I can provide more information.  Thanks in advance!

---

### Post by chili555 on 2014-03-21
> Any thoughts on what could be causing this issue?Possibly. When you set up a static IP address in /etc/network/interfaces, you are expected to set the address, gateway, et al as well as DNS nameservers. You have no DNS nameservers set. Also, your file is a bit busy. I suggest:```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.11.8
netmask 255.255.255.0
gateway 192.168.11.1
dns-nameservers 8.8.8.8 192.168.11.1
```Restart the interface to get the system to re-read and use the changes.```
sudo ifdown eth0 && sudo ifup -v eth0
```See if you are connected to the internet:```
ping -c3 www.google.com
```

---

### Post by vince8 on 2014-03-22
That did the trick, thanks!

---

### Post by chili555 on 2014-03-22
Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

