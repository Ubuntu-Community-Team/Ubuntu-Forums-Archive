---
title: "Routing between two networks"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by jstockamp on 2006-12-07
I am trying to set up a linux box as a router between two networks.  I have two networks (10.0.0.0/16 and 10.173.0.0/16).  My linux box (6.10) has 2 network cards:

eth0 = 10.0.0.45 MASK 255.255.0.0
eth1 = 10.173.0.45 MASK 255.255.0.0

I have enabled ip fowarding and can ping hosts on both networks from the linux box.

My hosts on the 10.0.0.0 network are configured to use a gateway of 10.0.0.248 (which is a firewall).  I have added a route to the 10.0.0.248 firewall for the 10.173.0.0/16 network to go to 10.0.0.45.  That part seems to be working ... I can ping hosts on the 10.173.0.0 network from the 10.0.0.0 network, so it looks like IP forwarding is working.

The problem is that I cannot ping hosts on the 10.0.0.0 network from the 10.173.0.0 network.  Any idea why this would be?  I can add a route entry for 10.173.0.0 MASK 255.255.0.0 GW 10.0.0.45 to hosts on the 10.0.0.0 network and then the ping will work, but I don't want to add this entry to all my hosts.

Any ideas why this isn't working?

Here's the results of ip addr show:
 
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth1: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:08:54:27:55:18 brd ff:ff:ff:ff:ff:ff
    inet 10.173.0.45/16 brd 10.173.255.255 scope global eth1
    inet6 fe80::208:54ff:fe27:5518/64 scope link
       valid_lft forever preferred_lft forever
3: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0b:db:28:ed:d4 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.45/16 brd 10.0.255.255 scope global eth0
    inet6 fe80::20b:dbff:fe28:edd4/64 scope link
       valid_lft forever preferred_lft forever

and ip route show:

10.0.0.0/16 dev eth0  proto kernel  scope link  src 10.0.0.45
10.173.0.0/16 dev eth1  proto kernel  scope link  src 10.173.0.45
default via 10.0.0.248 dev eth0

Thanks for any help you can offer.

- Jeff

---

### Post by mips on 2006-12-07
It's late and my eyes hurt, i'm off to bed but in the mean time have a look  at the following, maybe you can pick something up.

[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)
[http://ubuntuforums.org/showthread.php?t=89320](http://ubuntuforums.org/showthread.php?t=89320)

---

### Post by FrodoB on 2006-12-07
Also see:

[http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge)

---

### Post by jstockamp on 2006-12-07
Thanks, but I'm trying to route, not bridge.

---

### Post by linuchsan on 2006-12-07
it would be nice to see your routing table

---

### Post by FrodoB on 2006-12-07
[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

---

### Post by FrodoB on 2006-12-07
Also see:

/etc/sysctl.conf 

and 

man sysctl

---

### Post by mips on 2006-12-08
post output of:

cat /etc/network/interfaces
route -n

---

### Post by jstockamp on 2006-12-08
Here's /etc/network/interfaces:

[INDENT]auto lo[/INDENT][INDENT]iface lo inet loopback[/INDENT]

[INDENT]auto eth0[/INDENT][INDENT]iface eth0 inet static[/INDENT][INDENT]address 10.0.0.45[/INDENT][INDENT]netmask 255.255.0.0[/INDENT][INDENT]gateway 10.0.0.248[/INDENT]

[INDENT]auto eth1[/INDENT][INDENT]iface eth1 inet static[/INDENT][INDENT]address 10.173.0.45[/INDENT][INDENT]netmask 255.255.0.0[/INDENT]

[INDENT]auto eth2[/INDENT][INDENT]iface eth2 inet dhcp[/INDENT]

[INDENT]auto ath0[/INDENT][INDENT]iface ath0 inet dhcp[/INDENT]

[INDENT]auto wlan0[/INDENT][INDENT]iface wlan0 inet dhcp[/INDENT]And Here's route -n

[INDENT][FONT=Courier New][SIZE=2]Kernel IP routing table[/SIZE][/FONT][/INDENT]

[INDENT][SIZE=2][FONT=Courier New]Destination Gateway Genmask Flags Metric Ref Use Iface[/FONT][/SIZE][/INDENT]

[INDENT][SIZE=2][FONT=Courier New]10.0.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0[/FONT][/SIZE][/INDENT]

[INDENT][SIZE=2][FONT=Courier New]10.173.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth1[/FONT][/SIZE][/INDENT]

[INDENT][SIZE=2][FONT=Courier New]0.0.0.0 10.0.0.248 0.0.0.0 UG 0 0 0 eth0[/FONT][/SIZE][/INDENT]
 
[FONT=Courier New][SIZE=2]Thanks for your help.[/SIZE][/FONT]

[FONT=Courier New][SIZE=2]- Jeff[/SIZE][/FONT]

---

### Post by jstockamp on 2006-12-11
Any Ideas anyone?

---

### Post by mips on 2006-12-12
My setup is identical to yours and I can ping hosts on both sides.

The only difference in config is that I have a gateway specified for eth1:
In your case it would be:
```
auto eth1
iface eth1 inet static
address 10.173.0.45
netmask 255.255.0.0
gateway 10.0.0.45
```

---

### Post by FrodoB on 2006-12-12
Have you enabled ip forwarding in the kernel?
 
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
 
If this works you will need to put echo 1 > /proc/sys/net/ipv4/ip_forward
in a startup script.

---

