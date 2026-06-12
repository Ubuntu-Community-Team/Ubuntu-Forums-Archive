---
title: "Server pings local but won't ping outside"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by flyinggreg on 2008-07-27
Hi

I am a newb with enough knowledge to get in trouble!  I am running Ubuntu Hardy Server.

I was trying to reconfigure Apache2 and lost my default file.  So I decided to 'attempt' to reinstall Apache2 through apt-get and deleting the /etc/apache2 directory.  For some reason, I have lost my internet access only from my server.

I have a DSL connection and all the other computers connected access the internet with no problem.  My server is the only one that cannot access the internet.  From the server I can ping all across the network and can ping the router.  But I cannot ping outside the router ONLY FROM THE SERVER!  I tried [www.google.com](www.google.com) and ping 72.14.207.99 - neither work. My /etc/resolv.conf still shows 'nameserver 192.168.1.254' so I know that's ok.

Thanks for the help!

---

### Post by SpaceTeddy on 2008-07-27
this sounds a lot like you lost your default route for some reason... 
can you please post the output of 
```
route -n
cat /etc/network/interfaces
```

hope we can figure this out.

PS: the first command will show your current routing table
the second will show the boot configuration of your network cards.

---

### Post by flyinggreg on 2008-07-27
> **SpaceTeddy said:**
> this sounds a lot like you lost your default route for some reason... 
can you please post the output of 
```
route -n
cat /etc/network/interfaces
```

hope we can figure this out.

PS: the first command will show your current routing table
the second will show the boot configuration of your network cards.

Here's from route -n
```
root@wingandrotors:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

and here's /etc/network/interfaces
```
root@wingandrotors:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.65
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1

```

Thanks!

---

### Post by darkinnit on 2009-06-09
Not sure if this is still an issue for you, but I came across this post whilst having the same issue myself. I thought I should share my solution in case other people are finding this unanswered post.

For me it was a NAT issue. My firewall/router had not automatically set up either dynamic NAT or one to one NAT for the server that was experiencing the problem. Once I configured (in my case) one to one NAT for the server, it all started working. Setting up dynamic NAT would also solve it, but it depends on your needs.

---

### Post by superprash2003 on 2009-06-09
post output of **sudo iptables -L** from the terminal

---

