---
title: "dhcp / static ips"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by thesoupdragon on 2008-03-27
Hallo i have searched but not found a staisfactory answer - so here goes !

Ubuntu server working as lamp server, 

2 network cards -  eth0 - configured for dsl using ppp

eth1 configured at the moment static

iface eth1 inet static
        address 10.10.1.3
        netmask 255.255.255.0
        broadcast 10.10.1.255

I have 3 computers & printer which all have static ips and everything works fine BUT

I need to enable dhcp so that people can connect with laptops and not fiddle about with their network settings (ie work laptops so that they cant change them anyway)

Is this possible ? - and if so how ?

---

### Post by insineratehymn on 2008-03-27
Depends on whether you want to do it on your router or you want to have a server be the access point.

If you want your router to do it: 

Enable DHCP on your router using the class A addressing system.
Bind your wanted IP's to the chosen computers via MAC binding.
The rest of the computers that connect will be given an IP in ascending denominations after your last binded one.

---

### Post by thesoupdragon on 2008-03-27
thats exactly what i want to do but in the server !

---

### Post by insineratehymn on 2008-03-27
Sorry, never set up a server to be a wireless access point. :(

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

That may get you started...

---

### Post by thesoupdragon on 2008-03-27
its not just meant for wireless !

I also want that anyone can just connect with an ethernet cable and be able to surf etc.

---

### Post by chilinski on 2008-03-27
First, I'd like to recommend webmin as a good tool for configuring things like DHCP.

Secondly, most routers that do DHCP will do it on both the wireless and wired "sides." Afterall, both the wireless and wired are usually on the same subnet.

If you turn on DHCP on the Linux box, you'll have to turn it off on the router because you'll create all kinds of nightmares if you try to run two DHCP servers on the same subnet.

If you want your wireless clients to be on a whole separate subnet than the wired clients, then it's a different setup.

---

### Post by thesoupdragon on 2008-03-27
to clear up misunderstandings 

I am using the server as a router ! 
The server is connected over eth0 direct to the dsl and then functioning as a router - the second network card is connected to a 8 port switch.

The routing, masquerading etc is functioning fine using static ips, all i want to do is allow dhcp for unknown connections on the second network card eth1

I think its got something to do with setting the static ips to specific mac addresses on the other computers (ie the static ip's) and then letting dhcp deal with anything else.

---

### Post by Eiríkr on 2008-03-27
As another point on the graph, it's also possible to have a server with a fixed IP and let the router handle DHCP for other machines, which is precisely what I have set up here at home.  Many consumer router DHCP servers allow you to configure the address ranges used for DHCP, so you can simply set your static server IP outside of that range to avoid any IP address collisions.  

Cheers,

Eiríkr

---

