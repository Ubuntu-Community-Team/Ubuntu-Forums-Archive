---
title: "DHCP Server setup"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by jeremy12 on 2007-05-18
ok, i am guessing i am missing something simple

i am trying to turn my linux server into a router as well because well simply linksys crashes to much with all the traffic i put though it

the box has 2 ethernet cards eth0 and eth1

eth0 - Internet connection
eth1 - goes to a switch and on tot he rest of my network


i used the dhcp setup located on [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

it works fine my linux and windows pc's get a ip from the linux server via the switch i can ping and access the websites located on the linux box, however i cannot get past the server i am guessing i need to add a route or bridge, but what is the diffrence? i have been reading so much on the 2 i still dont fully understand how to read the setup lines, i can ping ubuntu.com from the linux server but not from anything behind the server

my main source on route setups has been [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#How_to_Configure_Two_Gateways](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#How_to_Configure_Two_Gateways)




My dchpd.conf
```
ddns-update-style none;
default-lease-time 600;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

ddns-update-style none;
subnet 192.168.0.0 netmask 255.255.255.0 {
	range 192.168.0.2 192.168.0.254;
	option subnet-mask 255.255.255.0;
	option broadcast-address 192.168.0.255;
	option routers 192.168.0.1;
	host box1 {
		hardware ethernet 00:19:21:25:9A:3A;
		fixed-address 192.168.0.200;
		}
	}
```

My /etc/network/interfaces
```

auto lo
iface lo inet lookpack

iface eth0 inet dhcp

auto eth0

iface eth1 inet static
address 192.168.0.1
network 182.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255

auto eth1

```

---

### Post by nixfaced on 2007-05-20
You didn't mention anything about NAT setup, so try the following on the gateway box:

sudo sysctl -w net.ipv4.ip_forward=1
sudo iptables -t nat -A POSTROUTING  -s 192.168.0.0/24 -i eth1 -j MASQUERADE

Or just use firestarter to set this up.

Also, I notice there's nothing about dns servers in your dhcp.conf, so if you haven't statically configured those on the client machines, that's something else to look at.

---

