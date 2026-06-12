---
title: "DHCP client and server"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by bmalp on 2006-07-27
Hi, 

my laptop connects via wlan card to the router (DHCP client). Now I want to connect the laptop to a settop box via a crossover cable. Like the laptop, the box should also be a DHCP client. 

Is this possible? So far, my trials were without success. Anyone able to help me out here?

Thanks!
Bmalp

---

### Post by philippe_carlo on 2006-07-27
I'm confused. You want to connect from the laptop to the box? Then the box must be a server, not a client.

---

### Post by bmalp on 2006-07-27
It looks like this:

Wireless router (DHCP server)
  |
  | eth2 (WLAN)
  |
Laptop (DHCP client)
  |
  | eth0 (LAN / crossover cable)
  |
Settop Box (DHCP client)

WLAN to laptop is OK, but box does not get an address.

---

### Post by mips on 2006-07-27
Then you should also make your laptop a dhcp server and assign an entire new network to the ethernet port.

---

### Post by hasimir44 on 2006-07-27
if you want the settop box to be able to get past the laptop, you'll also have to: 

1. enable ip forwarding on your laptop:

     sudo echo 1 > /proc/sys/net/ipv4/ip_forward

2. use iptables to route packets from the eth card through the wifi and vice versa.. 


i have this setup on my laptop, but i can't remember the iptables rules i used..

otherwise, it'd be easier to just use static ip addresses for the settop box and your laptop nic:

sudo ifconfig eth0 192.168.5.100     (on the laptop)
sudo ifconfig eth0 192.168.5.101     (on the settop box)

---

### Post by bmalp on 2006-07-28
Looks as if there is even a tool for this task:
[http://packages.ubuntulinux.org/dapper/source/guidedog](http://packages.ubuntulinux.org/dapper/source/guidedog)

Thanks to all who replied!

---

