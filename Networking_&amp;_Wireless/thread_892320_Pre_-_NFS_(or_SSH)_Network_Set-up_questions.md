---
title: "Pre - NFS (or SSH) Network Set-up questions"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by roundhay on 2008-08-17
Before I start to set up file sharing between my Ubuntu PC's at home I want to make sure that I get the basic's right.

Here is my set up:

Router (Wireless) attached to Cable Modem

I have 2 PC's, both running Hardy 8.04 attached to the router using network cables.

I have 2 work PC's which run Windows XP and connect to the router using wireless.

The Router and all of the PC's are currently set up to assign and accapet IP's using DHCP.

I want to be able to share files between the 2 Ubuntu PC's and still be able to connect the 2 work PC's to the router.

I have read a number of tutorials and how-to's but none of them clarify whether or not you need to set up a static IP network. I would like to understand how to set up the IP addresses and configure the router before I start with the NFS server and client set up.

I know these are basic questions but it is a long time since I have have to consider networking

---

### Post by ciryatan on 2008-08-17
Hello roundhay!

If I were you, I would set static IPs for all the computers which you want to share files with each other.
The DHCP server can still be running and assign IPs dynamically to all other computers except those.

Normally in your router configuration interface, there is the possibility to assign static ips to client computers, based on their MAC/HWaddr address.
(e.g. "eth0      Link encap:Ethernet  HWaddr 00:19:db:e7:55:7a"")
So they get always the same IP address by the dhcp server.

This makes it much easier for you to set up NFS server/client.

If you also want to share files with your windows computers, it might also be a good idea for them to have static ips.

greetz,
ciry

---

### Post by dmizer on 2008-08-17
Why not just configure your whole network for DHCP? There is nothing written that says you must use a static network for NFS. All you need is a way for Ubuntu to resolve local names.

I usualy use SAMBA for this task, but there are other ways as well.

---

### Post by roundhay on 2008-08-17
I have done some further reading today and have decided not to go with NFS and use SSH to set up my network. I plan to install Ubunti Server on a new machine in a couple of months and will need to use SSH to then so I may as well get started now.

To be more specific:

I do not mind setting up static IP's on the Ubuntu machines but I need the router to be DHCP so that my work lap tops can connect through the router. I have no Admin rights on these PC's and do not want to share files on them.

Can I have static IP's on my Ubuntu PC's (and sever when installed) and still run the router on DHCP?

I have tutorials covering fixed IP's and SSH installation but I'm not sure if I can keep the router on this setting?

---

### Post by bab1 on 2008-08-17
You can have both DHCP and static IP's in you network.  Keep the range of numbers used separate.  You can maintain DNS with the hosts files too.  I myself use the DNS server in my router.   

To set up a host statically you edit these 2 files:```
/etc/network/interfaces 
``` and ```
/etc/hosts
```

My interfaces file looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1

```

and my hosts file looks like this:```
127.0.0.1 localhost
192.168.1.12 whatever_you_call_your_computer
```

Make sure that the DHCP pool (range) of IP addresses does [COLOR="Red"]NOT[/COLOR] include the static hosts.  I use .50 to .150 for my DHCP pool.

---

### Post by roundhay on 2008-08-18
When you say DHCP server are you refering to the router?

---

### Post by bab1 on 2008-08-18
The router is the most likely place for the DHCP server to reside.  DHCP is a service that can be on other devices also.  If you have your wireless router setup to act as an AP then the modem could have the DHCP server there.  What is the topology (layout) of your network look like?  What are the modem and the router configurations like?  What are the IP addresses of the the 2 devices?

I'm not being picky, just trying to get you to think about the network from a design point of view.  These are the steps one takes BEFORE installing and modifying software.  Once you have decided on what and how you want to accomplish your goal, it won't be so confusing.

---

