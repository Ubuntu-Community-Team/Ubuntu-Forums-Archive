---
title: "Ping resolves Hostnames but not IPs"
date: 2015-11-13
forum: Networking &amp; Wireless
---

### Post by Ebahn13 on 2015-11-13
Backstory first: I'm brand new to Ubuntu (4 days of experience) and decided to set up a LAMP web server (via 15.10 desktop version) for me to play around with.
(My server is hooked up to my main PC through an ethernet cable, and then that tower is on the WiFi network. Also I don't have access to the router.)
I was trying to configure my DNS so that I can edit my site via the local IP (192.168.xxx.xxx) but restarting my tower changes it from how I had initially configured it, blocking access.
Pinging it fails, so I try with google.com.

```
ping -c 4 google.com

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 10.857/11.852/12.822/0.714 ms
```

Now, when I try to ping what I think is an IP that goes to google.com, it fails.

```
ping -c 4 64.233.160.0

--- 64.233.160.0 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms
```

Here is my /etc/networking/interfaces file

```
auto lo enp4s0
iface lo inet loopback

iface enp4s0 inet static
        address 192.168.137.14
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.137.255
        gateway 192.168.1.1
        dns-nameservers 8.8.8.8 8.8.4.4
```

My /etc/hosts file

```
127.0.0.1       localhost
127.0.1.1       devon-MCP73PVT-SM

192.168.137.14  testserver

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

And my /etc/resolv.conf

```
nameserver 192.168.137.1
nameserver 127.0.1.1
search mshome.net
```

Am I just missing something? Or am I going about it all wrong?

---

### Post by Ebahn13 on 2015-11-13
And a restart flips the problem, with IPs being resolved instead of Hostnames...
Modified /etc/networking/interfaces to

```
auto lo enp4s0
iface lo inet loopback

iface enp4s0 inet dhcp
```

At least it's progress...?

---

