---
title: "Automatic local and internet DNS resolving for local network server"
date: 2016-02-09
forum: Networking &amp; Wireless
---

### Post by macpoetter on 2016-02-09
Hello together!

I am right now working on my home network set up. Please see the image attached to get a general impression of what I am talking about.

[ATTACH=CONFIG]267209[/ATTACH]
My MacBook and my ubuntu are connected to my local network 192.168.1.0 with ethernet and wifi. My ubuntu itself makes a subnet with a dhcp server with the subnet 192.168.3.0. All this works fine and every device has in every possible setup configuration internet.
 
But when my iPhone logs in into the ubuntu wifi, and I want to reach [http://macbook.local](http://macbook.local), it is not able to resolve the name. If both are in the same network, however, for example iPhone and MacBook in ubuntu wifi or router wifi, then they can see each other. 

My /etc/dhcp/dhcpd.conf from the isc-dhcp-server package looks like this: 

```

[FONT=Menlo]# The ddns-updates-style parameter controls whether or not the server will[/FONT]
[FONT=Menlo]# attempt to do a DNS update when a lease is confirmed. We default to the[/FONT]
[FONT=Menlo]# behavior of the version 2 packages (’none’, since DHCP v2 didn’t[/FONT]
[FONT=Menlo]# have support for DDNS.)[/FONT]
[FONT=Menlo]ddns-update-style none;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# option definitions common to all supported networks…[/FONT]
[FONT=Menlo]option subnet-mask 255.255.255.0;[/FONT]
[FONT=Menlo]option broadcast-address 192.168.3.255;[/FONT]
[FONT=Menlo]option routers 192.168.3.1;[/FONT]
[FONT=Menlo]option domain-name "local";[/FONT]
[FONT=Menlo]option domain-name-servers 8.8.8.8, 8.8.4.4;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]default-lease-time 600;[/FONT]
[FONT=Menlo]max-lease-time 7200;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# If this DHCP server is the official DHCP server for the local[/FONT]
[FONT=Menlo]# network, the authoritative directive should be uncommented.[/FONT]
[FONT=Menlo]authoritative;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# Use this to send dhcp log messages to a different log file (you also[/FONT]
[FONT=Menlo]# have to hack syslog.conf to complete the redirection).[/FONT]
[FONT=Menlo]log-facility local7;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]subnet 192.168.3.0 netmask 255.255.255.0 {[/FONT]
[FONT=Menlo]range 192.168.3.10 192.168.3.100;[/FONT]
[FONT=Menlo]}[/FONT]

``` 
My /etc/rc.local looks like this: 

```

[FONT=Menlo]/sbin/iptables -P FORWARD ACCEPT[/FONT]
[FONT=Menlo]/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE[/FONT]
[FONT=Menlo]/sbin/modprobe ip_nat_pptp[/FONT]
[FONT=Menlo]/sbin/modprobe ip_conntrack_pptp[/FONT]

```

And I changed the following in /etc/sysctl.conf:

```

[FONT=Menlo]net.ipv4.ip_forward=1[/FONT]
[FONT=Menlo]vm.min_free_kbytes = 16384[/FONT]

```

Yesterday I also installed dnsmasq to use it as a DNS Server, but I don't really know if thats the right thing to do. The /etc/dnsmasq.conf file contains this:

```

# Set up your local domain here
domain=192.168.3.1
resolv-file=/etc/resolv.dnsmasq
min-port=4096
server=8.8.8.8
server=8.8.4.4


# Max cache size dnsmasq can give us, and we want all of it!
cache-size=10000

```

My /etc/resolv.conf contains only: nameserver 127.0.0.1.

I am working on this for a week now. It would be so awesome if someone would help me!!

Thanks a lot.

Best.

---

### Post by Doug S on 2016-02-10
Hi and welcome to Ubuntu forums,

You haven't explained why you want to have two sub-nets on your LAN. One obvious answer is to just use one sub-net. I also don't understand why you are loading the ip_nat_pptp and ip_conntrack_pptp modules.

---

### Post by macpoetter on 2016-02-12
Hi Doug S! Thanks a lot very reading my post and trying to help me!! I'm sorry that my introduction in the problem wasn't accurate enough. I will try to explain the "Big Picture". Please see an image attached, again :-)

[ATTACH=CONFIG]267255[/ATTACH]

The Ubuntu is actually also a OpenSSH VPN client, who is connected to a different network. This connection works. The goal is now, that the ubuntu is providing this tunnel to others via WiFi. Because for OpenSSH VPN I have to manually provide the IP for the Client in the Server network, I thought it would be the easiest if the Ubuntu client makes a DHCP server with NAT and provides this internet via routing tables to the Wifi clients. I would prefer if the Ubuntu client itself stays in its actual network, which means I don't change its default gateway or something that everything is just send over to the other network, just WiFi devices should do that. It works already that the wifi client devices can "see" the other MacBooks on the right with its IP. I can reach [http://macbook.local](http://macbook.local) with its local ip, but not with its name. The only "problem" left in my little network is the name resolution for the wifi clients.

The image before is the previous steps, before the tunnel is actually established. In my opinion this shows the same problem just in a bit easier. But if you say I can achieve my goal above differently, then I'm more then very very willing to change it.

[COLOR=#000000]I loaded the ip_nat_pptp and ip_conntrack_pptp modules, because one of the computers in the other network is a PPTP VPN Server and I would like the wifi devices to be able to make an additional VPN tunnel if they want to. These to lines were the result of a google research regarding PPTP Passthrough :)

Thanks again for your help. I really appreciate it.

Best[/COLOR]

---

### Post by macpoetter on 2016-02-16
No one knows an answer? Is my thought so strange to "forward" the DNS requests? I would be very thankful for any idea!

---

### Post by Doug S on 2016-02-17
> **macpoetter said:**
> No one knows an answer? Is my thought so strange to "forward" the DNS requests? I would be very thankful for any idea!Myself, I don't know what to suggest. I would perhaps try to make the Ubuntu server the master DNS and DHCP server for both sub-nets, making your store bought router, just a router.

---

