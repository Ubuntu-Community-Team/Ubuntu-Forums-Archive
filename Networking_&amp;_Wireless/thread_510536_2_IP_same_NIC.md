---
title: "2 IP same NIC"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by haky_h on 2007-07-26
I have a problem. I want to allow to IPs on the same NIC. I receive traffic from ISP on a cable with is plugged in a switch, from this switch the traffic comes to my ubuntu on a cable at IP address 192.168.1.2, and I want to make a second connection on the same cable with IP address: 172.16.12.1 to allow connection to internet to other computer which is connected to the same switch.
My /etc/network/interfaces is like:

iface eth0:1 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
network 192.168.1.0

iface eth0:2 inet static
address 172.16.12.1
netmask 255.255.255.128
broadcast 172.16.12.127


The problem is : it isn't work internet on my ubuntu. 
If you have any response, i will be very glad.

---

### Post by swampdweller on 2007-07-26
I'm guessing that the only reason you haven't received a
response is that people can't quite understand what you're
asking.

It sounds like you already have a gateway (192.168.1.1 on the
LAN side) and that you are plugged into this gateway as
192.168.1.2

You say the other computer is also plugged into the gateway,
so presumably it's on the same subnet, thus 192.168.1.???

What is 172.16.12.1?  Naively assuming a simple setup, I'd have
guessed that was your external internet address (the WAN side
of your gateway).

But I get the impression you're asking about something beyond
the basic setup.  I'm just not sure what.    :)

---

### Post by tact on 2007-07-27
A guide like this might help you....

[http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html)

---

