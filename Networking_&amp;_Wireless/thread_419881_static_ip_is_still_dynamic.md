---
title: "static ip is still dynamic"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Elisei on 2007-04-23
hello; i am using ubuntu 7.04 (great os) and im trying to get an ip addres to work statically;
i am trying to set it to 192.168.1.100 but for some reason i get 192.168.1.101;
my interfaces file looks like this:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

when i save this configuration i enter : sudo ifdown eth0  ;
                                                                       sudo ifup eth0       ;

                                                                       and my ip address is 192.168.1.101  ;

any suggestions are appreciated;

---

### Post by spd106 on 2007-04-24
Make sure that you have roaming mode turned off and that there are no other hosts on the network with the same IP address.

---

### Post by dbott67 on 2007-04-24
Are you using Network Manager or other similar program?

---

