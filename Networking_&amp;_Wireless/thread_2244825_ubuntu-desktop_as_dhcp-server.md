---
title: "ubuntu-desktop as dhcp-server"
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by razvan4 on 2014-09-19
Hy. Our server debian 6 from the office for some reasons is down.I  installed ubuntu to one computer and we want to set a dhcp server to  route our external ip address to 4 computers  by a second network card  and a switch and portforward some specific ports. I need some help with  dhcpd.conf and inferfaces file. We want to route a subnet like 192.168.0.50,  192.168.0.51 etc and portforward a specific port. 
Sample:
subnet 192.168.0.1 netmask 255.255.255.0 { 
range 192.168.0.50 192.168.0.80; //range of ip addresses for clients
default-lease-time 60;  //just for test 
max-lease-time 120;  //just for test
option routers 192.168.0.1; //default gateway for the client pc
option broadcast-address 192.168.1.255;
option subnet-mask 255.255.255.0;
option domain-name-servers 123.123.123.123; //dns 
}
we want the client pc like this 
ip     192.168.0.50
netmask 255.255.255.0
gateway 192.168.0.1

any other settings that i am missing ??

---

