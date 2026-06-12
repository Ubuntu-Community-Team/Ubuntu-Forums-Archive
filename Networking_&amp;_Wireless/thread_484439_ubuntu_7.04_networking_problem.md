---
title: "ubuntu 7.04 networking problem"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by ovidiupys on 2007-06-25
hi. i just installed ubuntu 7.04. i configured /etc/network/interfaces like this :

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
	
auto eth1
iface eth1 inet static
	address 192.168.1.1
	netmask 255.255.255.0
	dns-nameservers 82.77.192.51 213.157.173.130

then i executed some commands for network sharing :
modprobe iptable_nat
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

i get the right ips when i do #ifconfig -a on both nix

when i ping an external ip or the gateway or the dns server it works, but when i try to ping the computer inside the network it doesn't work, although if i ping 192.168.1.1 fom the computer inside the network , the router responds.

what do i have to do to make it work ?

---

### Post by spd106 on 2007-07-05
That's a very nice post with lot's of detail, but you don't explain what your trying to do, nor do you describe the physical setup. So it's difficult to analyze exactly what is going wrong.

Do you have route/gateway set up for the external PC to point the ping packets at the router? Something like this```

sudo ip route add to 192.168.1.0/24 via <insert router's eth0 address from dhcp> dev eth0
```

As you have not added any firewall type rules to drop packets, they should still be routed.

---

