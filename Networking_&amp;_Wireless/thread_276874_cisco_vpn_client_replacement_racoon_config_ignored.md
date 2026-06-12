---
title: "cisco vpn client replacement racoon: config ignored"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by tjr on 2006-10-13
Hi, as there is no cisco vpnclient for linux/ppc, I'm trying to use racoon/ipsec-tools.


My problem is very elementary: /etc/racoon/racoon.conf is never honored. Some script creates a custom racoon.conf in /var from mine  and starts racoon with it -- omitting all of my entries. This even happens with the examples provided in /usr/share/racoon/*/roadwarrior/client.

I installed racoon with manual editing of /etc/racoon.conf enabled.

Basically, my system is dapper 6.06.1LTS fresh from DVD (except for  my own config work) and apt-get update'd mid-september. If this problem is solved by an update, please tell me exactly which packages to update, as I have no internet access from linux without cisco vpn.


Alternatively, how do you start racoon manually (without init scripts)? Just typing
"modprobe crc32c ipcomp6; racoon -d -v &"
as root does start it, but gives "bad file handle" when trying to do
"racoonctl vpn-connect myuser gateway_ip"
. Output in /var/log/syslog is not helpful.


Any help is appreciated. Basically I'm trying to connect to a Cisco VPN Concentrator network using rsa certificates and xauth, but first, racoon should start up.
(network details in German: [http://cert.uni-stuttgart.de/files/fw/vpn-concentrator-xauth-kochrezept.txt](http://cert.uni-stuttgart.de/files/fw/vpn-concentrator-xauth-kochrezept.txt))
(it should work: [http://www.lacave.net/~fred/racoon/interop.html](http://www.lacave.net/~fred/racoon/interop.html))

---

### Post by meng on 2006-10-13
This is a Cisco VPN client for Linux (not necessarily PPC though), but in any case I wouldn't recommend it for x86 either. What about vpnc? This is available through repositories, compatible with Cisco concentrators and is very easy to set up, there is also a lots of help available through google and these forums on setting it up.

---

### Post by tjr on 2006-10-14
vpnc cannot do certificates, but my unversity uses just that. And cisco vpnclient isn't available for linux/ppc.
That pretty much leaves me with ipsectools/racoon. According to their interoperability chart, it should work.

---

