---
title: "Bridging 2 NIC"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by swamyveera on 2007-04-05
Hi there,
 I desperately need some help here.
 I have a ubuntu machine, which i would like to act as a bridge between 2 network classes.
 I have a network in the range 192.168.1.x and another network in the range 10.0.0.x - I am planning to have a ubuntu machine, which can act as a bridge between these 2 networks.

Infact, this ubuntu machine  is planned to connect to a web server on the 192.x.x.x. network and the client machines with browsers on the 10.x.x.x network.

Honestly, i dont even know where to start, just installed ubuntu, had 2 network cards installed and what do i do next? 

Any kind of help is highly appreciated.

Thanks

---

### Post by abazimi on 2007-04-11
hi swamyveera
you should use of *brctl* command
so at first install *bridge-utils* package, it contains brctl
	[B]sudo aptitude update
	sudo aptitude install bridge-utils
[/B]
imagin that you whant make a bridge with "mybridge" name and you have 2 NIC interfaces with "eth0" and "eth1" names.
then for configuring your bridge follow these commands:
        [B]sudo brctl addbr mybridge
	sudo brctl addif eth0
	sudo brctl addif eth1
	ifconfig eth0 0.0.0.0
	ifconfig eth1 0.0.0.0[/B]
	now give IP to the bridge: 
	for Static configuration:
	i**fconfig mybridge up 192.168.0.3 netmask 255.255.255.0**
	for DHCP:
	**ifconfig mybridge up**
	if you need to have a default gatewayroute 
	**route add default gw 192.168.0.1**
	and for DNS:
	You may also need to add your DNS servers to /etc/resolv.conf if you are using a static IP (this is a 	one time thing): 
	[B]nameserver xxx.xxx.xxx.xxx
	nameserver xxx.xxx.xxx.xxx[/B]

[COLOR="DarkRed"]also you may refere to this page for more information:[/COLOR]
[http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge)

---

### Post by abazimi on 2007-04-11
and for permanent Configuration edit /etc/rc.local and add folowing commands 
	ifconfig eth0 0.0.0.0
	ifconfig eth1 0.0.0.0
	brctl addbr mybridge
	brctl addif mybridge eth0
	brctl addif mybridge eth1
	ifconfig mybridge up 192.168.0.8 netmask 255.255.255.0
	route add default 192.168.0.1

in this way when your restart your computer all the configuration will be added and your bridge will be ready

---

