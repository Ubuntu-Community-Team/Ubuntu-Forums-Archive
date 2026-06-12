---
title: "Two interfaces, both auto, second won't come up on reboot"
date: 2017-10-16
forum: Networking &amp; Wireless
---

### Post by norviller on 2017-10-16
Running Ubuntu 16.04 server and having an issue with my network interfaces.  The system pretty much works great but when I reboot the second interface won't automatically come up.  For context I have a WAN interface (enp1s0, DHCP, works perfectly) and a LAN interface (enp2s0, static, not so perfect).  The LAN interface shows down after a reboot and stays that way until i run "sudu ifup enp2s0".  After that all is well...

Here's the contents of /etc/network/interface -

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
# WAN interface port labeled 1
auto enp1s0
iface enp1s0 inet dhcp


# LAN interface port labeled 4
auto enp2s0
iface enp2s0 inet static
    address 10.0.0.1
    netmask 255.255.255.0
#    broadcast 10.0.0.255
#    network 10.0.0.0


# Port labeled 3
#auto enp4s0
#iface enp4s0 inet dhcp


# Port labeled 2
#auto enp3s0
#iface enp3s0 inet dhcp

```

[FONT=Verdana]Any ideas on what to look for?  I added the broadcast and network statements based on another post.  Didn't make a difference in the issue so I commented them out.

[/FONT]

---

