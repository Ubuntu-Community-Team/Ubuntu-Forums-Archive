---
title: "Ubuntu - Why is there no info in my /etc/network/interfaces file"
date: 2013-11-27
forum: Networking &amp; Wireless
---

### Post by frogwarrior on 2013-11-27
I'm following a tutorial, and they tell me to edit the /etc/network/interfaces file, they say it should look like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
## This device provides internet access.
iface eth0 inet static
  address 192.168.1.10
  netmask 255.255.255.0
  gateway 192.168.1.1
```
but my interfaces file actually contains this:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

I've on Ubuntu 13.10, but I've come across this problem before in older versions of Ubuntu. Why doesn't my interfaces file contain any relevant information? The tutorial I'm following is:
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
I want to use openvpn with my ipredator account, because I hear openvpn is more secure than pptp.

---

### Post by steeldriver on 2013-11-27
The /etc/network/interfaces file is used by the older networking service - newer desktop versions use a service called network-manager which has its own configuration files in /etc/NetworkManager

If you are trying to set up a static LAN IP with Network Manager you should use the GUI applet (or start the connection editor from a terminal using the 'nm-connection-editor' command) and go to the 'Ipv4 Settings' tab, where you can change the method from 'DHCP' to 'Manual' and fill in the IP and netmask details in the boxes provided.

---

### Post by frogwarrior on 2013-11-27
Actually what I wanna do is get a shell script to add new VPN connections for me. I can add PPTP connections through the network-manager GUI, but I can't figure out how to do it with the command line. Is there a way to do it with nmcli?

---

