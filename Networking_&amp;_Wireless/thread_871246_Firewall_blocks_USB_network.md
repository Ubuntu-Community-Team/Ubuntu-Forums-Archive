---
title: "Firewall blocks USB network"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by sderrick on 2008-07-26
Hardy Heron

I am connecting to a phone using the usb networking.  I can also connect to the internet from the phone using ip_forwarding on my ubuntu host. It works fine as long as my firewall is off. 

here is my interface config for USB0

auto usb0
iface usb0 inet static
	address 192.168.0.200
        netmask 255.255.255.0
        network 192.168.0.0
        up iptables -A POSTROUTING -t nat -j MASQUERADE -s 192.168.0.0/24 &
        up echo 1 > /proc/sys/net/ipv4/ip_forward &
        up iptables -P FORWARD ACCEPT &
        down iptables -D POSTROUTING -t nat -j MASQUERADE -s 192.168.0.0/24 &

how can I configure the firewall tp allow not block this traffic?

thanks,  Scott

---

