---
title: "eth0 doesn't show inet ip"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by vitor4 on 2014-03-08
Sorry my english is bad;
I basically need the eth0 IP so I can edit the index.html on my server and put content in there, but when I do 'ip addr show' it only shows the following:

$ip addr show
1: lo: .......... (random stuff)
inet  127.0.0.1/8 scope host lo

2:eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 ...(random stuff)
link/ether 08:00:27....................................................
inet6 fe80::-------------------------------------------

I've been following this video to set up my web server, but when this guy does 'ip addr show' it comes up with the eth0 IP address and he can access the page, and I can't. 
[http://www.youtube.com/watch?feature=player_detailpage&v=Ykt3MeNwORQ#t=501](http://www.youtube.com/watch?feature=player_detailpage&v=Ykt3MeNwORQ#t=501)

---

### Post by Iowan on 2014-03-08
**ifconfig** is what I usually use to see how interfaces are configured.
**ifconfig -a** will show all interfaces - even if they are not active.

---

### Post by vitor4 on 2014-03-08
ifconfig returns the same.
says my inet is 127.0.0.1

---

### Post by Iowan on 2014-03-08
That's probably for the loopback device (lo).
Is eth0 set up in */etc/network/interfaces*?

Moved to  Networking & Wireless

---

### Post by vitor4 on 2014-03-08
Ye sorry, the 127.0.0.1 appears on the Local loopback;

On eth0:
Link encap: Ethernet HWaddr: 08:00:27.........
inet6addr: fe80:27ff:fe40:191c........


how do i check if eth0 is set up in /etc/network/interfaces?

---

### Post by steeldriver on 2014-03-08
It looks like your eth0 is using ipv6 only (no ipv4 address is assigned)?

---

### Post by vitor4 on 2014-03-08
can i set eth0 to ipv4 then? sorry im a complete newbie when it comes to networks

---

### Post by Iowan on 2014-03-08
> **vitor4 said:**
> how do i check if eth0 is set up in /etc/network/interfaces?
```
cat /etc/network/interfaces
```
T'would be good if you could post the results...

---

### Post by vitor4 on 2014-03-08
```
# The loopback network interfaces
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 intet dhcp
```



Btw im running this on virtualbox

---

### Post by Iowan on 2014-03-08
I presume this was hand-copied... if not:
```
iface eth0 [COLOR="#FF0000"]intet[/COLOR] dhcp
```

I haven't yet become familiar with virtualbox. :(
Realize that a DHCP address can change periodically unless the DHCP server is set to issue a static lease.

---

### Post by vitor4 on 2014-03-08
Ye, it was hand copied. It actually says inet

---

### Post by varunendra on 2014-03-08
While or after creating the Virtual Machine, what kind of networking have you selected? NAT? Bridged? Host only or something else?
Any Advanced settings on the virtual adapter?
Can you post the screenshot of the Network Settings of the VM? With Advanced settings expanded.

And does this VM contain a client or the server itself?

From the discussion so far, it seem it is the server on which you want to work. If so, which machine do you want to access it? From 'Any' machine on the network or just the Host on which it is installed?

---

