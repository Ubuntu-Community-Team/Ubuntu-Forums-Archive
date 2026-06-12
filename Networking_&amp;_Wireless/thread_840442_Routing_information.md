---
title: "Routing information"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by e-tip on 2008-06-25
Hi all, i'm having some problems on configuring my pc to use multiple virtual interfaces.
My situation is : i've got one pc with one ethernet card.
I've 6 ADSL lines. For each of this lines i need to control if the line is up and running. To do this i've done a script that tries to ping one host and checks if the response is good or not.
Up to now i had 6 pcs configured and this script were running in those machines but for problems i had to renounce to 5 machines.
My idea was to set up virtual interfaces in the remaining machine and passing to ping -I switch use the virtual ifaces.
But.. is there a way to use a different router if the traffic is from virtual interfaces
ex.
eth0:1 address 88.xx.xx.65 router 88.xx.xx.64
eth0:2 address 87.xx.xx.84 router 87.xx.xx.63
ping -I eth0:1 packet sould be routed to 88.xx.xx.64
ping -I eth0:2 packet should be routed to 87.xx.xx.63
(i forgot to say.. ip address are public )
is there any way to do it ? 
Thanks in advance

---

### Post by ilrudie on 2008-06-25
Yes.  Use the route command to setup temporary routes.  You can say for this host or network send the packets to this gateway over this device.  Read the man pages for route for more detail but:

route add -net <network_ip> netmask <netmask> gw <gateway_address> dev <device>

to make this permanent once you know they are working the way you want add them to /etc/network/interfaces under the stanza for the correct interface like so:

up route add -net <network_ip> netmask <netmask> gw <gateway_address> dev <device>

---

### Post by e-tip on 2008-06-25
That's great, i've misunderstand the meaning of -net in man page of route command, tomorrow i'm trying and i'll let you know.
thank you so much

---

### Post by e-tip on 2008-06-26
Well, i've done some tests, but it doesn't work like i suppose to...
the situation...:
```
tiziano@morpheus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:63:a0:f2:a0
          inet addr:192.168.50.30  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21b:63ff:fea0:f2a0/64 Scope:Link
<cut>
eth0:2    Link encap:Ethernet  HWaddr 00:1b:63:a0:f2:a0
          inet addr:88.xxx.xxx.226  Bcast:88.xxx.xxx.231 Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17
```
And this is the route command
```
tiziano@morpheus:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
88.xxx.xxx.224    host225-xxx-stat 255.255.255.248 UG    0      0        0 eth0
88.xxx.xxx.224    *               255.255.255.248 U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.0.0     *               255.255.0.0     U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```
But when i try to check if everything is working with this command
```
wget --bind-address=88.xxx.xxx.226 whatismyip.org
```
the address shown is the one associated to 192.168.1.1 router

did i forget something ?
thanks in advance

---

### Post by ilrudie on 2008-06-26
Its probably because whatsmyip.org isnt in your routing tables so it is using the default route.  Try 
```

route add -host 208.79.211.77 gw host255-xxx-stat 

``` or ```

route add -host whatsmyip.org gw host255-xxx-stat

```Do you now get an IP address that looks like its coming from the other gateway?

---

### Post by e-tip on 2008-06-26
It worked now, thanks
Only "bad" thing is that i need to define one route rule for each line that i have to check, no need to use particular switches in ping command. that's cool

---

### Post by ilrudie on 2008-06-26
Glad to be of service.  

The box will select the first destination that matches and use that route so you can't set up 6 different routes to the same destination and access it different ways.  This may not be a problem for you but if part of your test involves checking the ip at whatsmyip.org then you will need to add and delete the routes for each test.  To best do that just set up a shell/perl script that adds the route, runs the tests, deletes the route and then does it over again for the next test.  If you want some help just post back and I will help you write one up.  It will probably need to be done as root but you can give the file root-only write and set up sudo to allow running the script as root without a password once you like the way the script is working.

---

