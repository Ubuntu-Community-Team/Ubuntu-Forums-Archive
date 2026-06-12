---
title: "DNSMASQ and Forwarding with IPTABLES"
date: 2015-09-28
forum: Networking &amp; Wireless
---

### Post by bbruecker on 2015-09-28
This is my situation:
```
Internet <---> Router-from-ISP         Ubuntu-Router (DNSMASQ)
               192.168.0.1     <-----> 192.168.0.253 (br0:1)
               Web-Server         |    192.168.1.1 (br0)       <---> Clients
               192.168.0.2     <---                                  192.168.1.100-192.168.1.100.150
```
I would like to bring clients form 192.168.1.x network via Ubuntu router (12.04) to the internet. I have learned, it is not possible to connect the clients to the internet without masquerading if the ISP router is not allowing to add routes ([http://ubuntuforums.org/showthread.php?t=2295744](http://ubuntuforums.org/showthread.php?t=2295744)) -- which unfortunately is my case.

On the ubuntu router I added set up DNSMASQ and HOSTAPD. DNSMASQ is distributing IPs for wireless and wired clients (that's why I added a bridge and virtual interface).

Wish list:
[LIST=1]
[*]clients from 192.168.1.x subnet should be able to use internet 
[*]clients from 192.168.1.x subnet should access the Router from ISP and the web server 
[*]some internet addresses should be blocked for 192.168.1.x clients by DNSMASQs "manipulating" feature, e.g. (address="/facebook.com/172.0.0.1"). 
[/LIST]
I'm not expert for IP tables, but I found this example -- which somehow works:```
sudo iptables -A FORWARD -o br0:1 -i br0 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
```
I don't understand why, but dnsmasq needs to be restarted.

Result is --lets say it works (in lot of cases):
[LIST=1]
[*]DHCP works for wireless and wired clients 
[*]Linux clients can access webserver, IPS router and the internet. 
[*]Some android devices can access the internet/some not (but this is maybe or hopefully a different problem). 
[/LIST]
Problem/symptoms: The blocking mechanism of DNSMASQ is not working; maybe the DNS cache is not accessed by the clients. Traceroute gives my Ubuntu Router as the first hop, but clients can ping facebook.com by facebooks real IP address (not my fake). So it seems to me, either I didn't set up DNSMASQ properly or my IPTABLES are somehow circumventing the DNSMASQ (some config files below).

I think this indicates, I did some mistake. Here is my configuration:

dnsmasq.conf:```

address=/facebook.com/127.0.0.1
interface=lo
interface=br0
dhcp-range=192.168.2.200,192.168.2.250,255.255.255.0,12h
```

Interfaces:```

auto lo
iface lo inet loopback
auto br0
iface br0 inet static
    bridge_ports p1p1 wlan1
        address 192.168.2.1
        network 192.168.2.0
        netmask 255.255.255.0
auto br0:1
iface br0:1 inet static
        address 192.168.0.253
        netmask 255.255.255.0
        gateway 192.168.0.1
```

Resolf.conf:```

nameserver 127.0.0.1
nameserver 172.0.0.1
nameserver 192.168.0.1
```

Maybe someone is able to find my mistake... Or maybe It's not possible to use masquarading with DNSMASQ (to use DNSMASQs DNS cache)?

---

### Post by bbruecker on 2015-09-29
I found one small mistake in interfaces: I was putting the gateway to br0, but the gateway is in the 192.168.0.x subnet. I changed the previous post according to the new settings. Well I think it doesn't matter, because the gateway is for the machine not the interface... Correct me, if my guess is wrong.

My ISP changed without warning to **IPv6**. So the ISP router **was** distributing IPv6 addresses (until I turned of DHCP -- one of the few settings my ISP allows on their router). Could IPv6 disturb my Ubuntu router? And if, how can I deal with that? Does it help or destroy my configuration to turn of IPv6 on the Ubuntu router?

---

