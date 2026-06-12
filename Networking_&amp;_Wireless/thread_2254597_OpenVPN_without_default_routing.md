---
title: "OpenVPN without default routing"
date: 2014-11-28
forum: Networking &amp; Wireless
---

### Post by sparky-steve on 2014-11-28
Hello,


I'm new to customized openVPN, though I've used linux for over 10 years.


I usa HMAPro to secure my browsing when I'm out & about. When I connect everything is routed through the VPN.


However what I'd like to do is *not* change the default route, and instead have specific applications use tun0.


I've worked out that by using "route-noexec" in the .ovpn file, it will not change the default route.


This is the output of route before openvpn is run:


```
steve@X501A:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.6.1     0.0.0.0         UG    0      0        0 wlan0
192.168.6.0     *               255.255.255.0   U     9      0        0 wlan0
steve@X501A:~$ 

```


This is the output of route after openvpn is run, with "route-noexec" included


```
steve@X501A:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.6.1     0.0.0.0         UG    0      0        0 wlan0
10.200.0.0      *               255.255.252.0   U     0      0        0 tun0
192.168.6.0     *               255.255.255.0   U     9      0        0 wlan0
steve@X501A:~$ 

```


Which is what I thought I wanted; However I cannot ping anything through the tun0 interface:


```
steve@X501A:~$ ping www.google.com
PING www.google.com (74.125.228.243) 56(84) bytes of data.
64 bytes from iad23s24-in-f19.1e100.net (74.125.228.243): icmp_seq=1 ttl=53 time=23.8 ms
64 bytes from iad23s24-in-f19.1e100.net (74.125.228.243): icmp_seq=2 ttl=53 time=26.1 ms
64 bytes from iad23s24-in-f19.1e100.net (74.125.228.243): icmp_seq=3 ttl=53 time=26.3 ms
^C
--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 23.867/25.467/26.338/1.132 ms
steve@X501A:~$ ping www.google.com -I tun0
PING www.google.com (74.125.228.244) from 10.200.3.242 tun0: 56(84) bytes of data.
^C
--- www.google.com ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5040ms


steve@X501A:~$ 

```


If I run openvpn without "route-noexec" then the route output is as follows:


```
steve@X501A:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.200.0.1      128.0.0.0       UG    0      0        0 tun0
default         192.168.6.1     0.0.0.0         UG    0      0        0 wlan0
10.200.0.0      *               255.255.252.0   U     0      0        0 tun0
107.181.66.2    192.168.6.1     255.255.255.255 UGH   0      0        0 wlan0
128.0.0.0       10.200.0.1      128.0.0.0       UG    0      0        0 tun0
192.168.6.0     *               255.255.255.0   U     9      0        0 wlan0
steve@X501A:~$ 

```


And obviously, "ping [http://www.google.com](http://www.google.com) -I tun0" works with no problem.


OpenVPN adds the following routes:


```
/sbin/ip route add 107.181.66.2/32 via 192.168.6.1
/sbin/ip route add 0.0.0.0/1 via 10.200.0.1
/sbin/ip route add 128.0.0.0/1 via 10.200.0.1

```


If, after establishing tun0, I run each of these individually and then try "ping [http://www.google.com](http://www.google.com) -I tun0", I get nothing until I add the default route.


To summarize, I want to establish a VPN without changing the default route.  I have several applications which can manually select tun0, but thus far, tun0 seems to be unusable.


Many thanks in advance for any assistance!


Steve

---

### Post by SeijiSensei on 2014-11-29
Did you enable packet forwarding in /etc/sysctl.conf?  (Uncomment the line "net.ipv4.ip_forward=1".)

Did you set up "masquerading" by adding a rule to iptables like
```
/sbin/iptables -t nat  -A POSTROUTING -o wlan0 -j MASQUERADE
```

---

### Post by sparky-steve on 2014-12-06
I guess it's time to expand my original thread.

The box in question is a headless ubuntu server acting as a gateway/router/filter for the entire house; currently it has 3 networks, WAN, LAN & Wifi, via shorewall, dansguardian, squid et al.

I *guess* I could make shorewall a 4-interface system, and I dont know why I didn't think of that earlier.

When time allows, I'll try it out & report back!

SS

---

