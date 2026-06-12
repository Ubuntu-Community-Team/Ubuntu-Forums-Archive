---
title: "IP Address changes only after reboot"
date: 2016-08-01
forum: Networking &amp; Wireless
---

### Post by ismael-yanez on 2016-08-01
[SIZE=2]Hello I have the following problem:

I have a virtual machine, where I installed Ubuntu Server 16.04 with OpenSSH and Standard System Utilities. This is the /etc/network/interfaces configuration.

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ens160
     iface ens160 inet static
     address 10.10.20.110
     netmask 255.255.255.0
     network 10.10.20.0
     broadcast 10.10.20.255
     gateway 10.10.20.254
     # dns-* options are implemented by the resolvconf package, if installed
     dns-nameservers 10.10.20.1 10.10.20.2

After that I change the IP address to 10.10.20.100 and after that I can only change the IP address if I restart the machine. ifdown ens160 && ifup ens160 doesn't work, ifconfig ens160 down and ifconfig ens160 up doesnt work, /etc/init.d/network restart doesn't work. When I do ifdown ens160 && ifup ens160 I get the following message: RTNETLINK answers: Cannot assign requested address

The strange thing is, that after I change the IP address in the [/SIZE]/etc/network/interfaces file but before rebooting, I can ping from another computer in the same network both IP addresses. I can confirm that this computer is reacting to both IP addresses, because when I shut it down, I can't ping none of them.[SIZE=2]

Does someone have an idea?

My virtual machine run under ESXi 5.5. Could that be it?

Thanks!
Ismael[/SIZE]

---

