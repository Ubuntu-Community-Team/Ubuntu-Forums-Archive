---
title: "Multiple network interfaces: ping sendmsg operation not permitted"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by I_want_to_write on 2007-01-24
Hi, 

I normally use my laptop's built-in wireless adapter but I have a MAC filter set for it and to get around the filter sometimes I use my ethernet card or an USB wireless adapter to connect. 

The problem I have is that, the network interface I want to use must be initialised at start-up, eg cable or usb should be plugged in. I've tried all sorts of different combinations to switch between interfaces without restarting the computer but I haven't been successful. 

Normally, I switch between interfaces using ifconfig up and down commands, eg: 
ifconfig wlan0 down        to disconnect the wireless
ifconfig eth0 up             to connect the ethernet 
dhclient  eth0                to get IP
the ethernet NIC gets an address but that's about it, it doesn't do anything afterwards. For example: 

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

I've tried "/etc/init.d/networking restart" as well, interfaces are turned off and on, dhcp gets IP addresses, ifconfig gives me IP addresses and shows me whats connected. But when I ping I get the same result. 

I've tried ifup, ifdown, etc the result is still the same. 

dmesg shows outgoing packets to DNS but nothing coming back. 

I remember when I first installed ubuntu I didn't have this problem, I don't know what's changed since. 

my /etc/network/interfaces file: 

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid deleted

regards

---

### Post by I_want_to_write on 2007-01-24
sorted

The problem was with the iptables 

I don't understand why ip rules are set to drop packets to and from new interfaces.

---

### Post by larytet on 2007-08-08
hello, may you add more details how you fixed iptables
thank you

---

### Post by larytet on 2007-08-08
ok. solved. in my case this was a shorewall installation. Just sudo apt-get remove shorewall

---

