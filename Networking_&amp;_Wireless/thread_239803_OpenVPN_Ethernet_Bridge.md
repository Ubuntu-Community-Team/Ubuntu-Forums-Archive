---
title: "OpenVPN Ethernet Bridge"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by fawwaz on 2006-08-19
Hi! I'm in trouble with OpenVPN eth bridge setup. Hope someone would help me on this.

Here is my home network setup:
broadband eth0> ubuntu box [apache/firewall/router/ftp/samba] > two ethernet cards > eth1-WinBox eth2-UbuntuBox

I had to edit this post so to be more specific on the subject. I was hoping to enable netbios through two bridged subnets. My final goal was to have secure netbios through vpn over the internet between my office and home. 

I did install OpenVPN, generated secure keys for server and clients, enabled modules and installed bridge-utils.

Now I believe my problem is due to routing. My setup: eth0 (internet dynamic dyndns), eth1 (10.0.1.1), eth2 (10.0.0.1). I did this:

brctl addbr br0
brctl addif br0 eth1
brctl addif br0 eth2
openvpn --mktun --dev tap0
brctl addif br0 tap0
ifconfig eth1 0.0.0.0 promisc up
ifconfig eth2 0.0.0.0 promisc up
ifconfig tap0 0.0.0.0 promisc up
ifconfig br0 192.168.0.235 netmask 255.255.255.0 broadcast 192.168.0.255

I'm pretty stuck here, clients cannot ping each other. I figure I should set dhcp3 to lease ip-s on newly created subnet bridge as I did earlier with eth1 and eth2. Clients still cannot ping each other.

---

