---
title: "convert a wireless-connected laptop to a wired router"
date: 2015-10-12
forum: Networking &amp; Wireless
---

### Post by esolve on 2015-10-12
I have two laptops, A and B
A is connected to wireless network (with fedora), and its IP address is 192.168.0.15
now I want to connect B(with Ubuntu) to a wired network, but my wireless router is not in my room,  it is not convenient to connect B to the router in wired style.
so I want to use A as a wired router for B
also I hope B is using the same private network as A (also with 192.168.0.*),

Note: I want to use libpcap/tcpdump on both A and B
also I need to use openvpn to create a tun virtual NIC on A

are there any solutions for this?
thanks!

---

### Post by SeijiSensei on 2015-10-12
First, you won't be able to use the same subnet for both sides of the router.  The wired connection between A and B needs to be in a different subnet and "masqueraded" to the upstream network, 192.168.0.0/24.

I have a similar arrangement with my LG TV wired to the computer which has a wifi connection to my router.  I use just a couple of simple commands to accomplish this. I've adapted the IPs to fit your network:

```

ifconfig eth0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255
iptables -t nat -F
iptables -t nat -A POSTROUTING -o wlan0 -j SNAT --to 192.168.0.15

```
The first command assigns the address 192.168.1.1 to the router's Ethernet port.  The next two use iptables to handle the masquerading.  The first clears any existing rules; the second tells the router to substitute its wireless address as the source IP for packets leaving the device.  (SNAT stands for "source network address translation".)  Assign eth0 on laptop B an address in 192.168.1.0/24.

If your computers' Ethernet ports are "auto-sensing," you can use a regular Ethernet cable to connect them.  Otherwise you'll need to use a "crossover" Ethernet cable, or buy a cheap network switch like [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704042").

You'll also need to enable packet forwarding by uncommenting the line
```
net.ipv4.ip_forward=1
```
in the file /etc/sysctl.conf and rebooting.

I don't know about tcpdump; I rarely use it.

Configuring OpenVPN depends on what you want to do with it.  I use it to create full-time tunnels between a server on my local network and my virtual servers at Linode.  Those kinds of simple tunnels can be set up with shared static keys.  See [http://openvpn.net/static.html](http://openvpn.net/static.html) for details.

---

