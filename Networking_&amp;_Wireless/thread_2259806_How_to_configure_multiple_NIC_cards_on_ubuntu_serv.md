---
title: "How to configure multiple NIC cards on ubuntu server 14.04 LTS and connect to router?"
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by anis-bedhiafi on 2015-01-07
Hi guys,

I have an HP hard Server on which I installed Ubuntu server 14.04 LTS. The server has two ethernet cards.
I installed Squid proxy server and I am using iptables as a firewall on my ubuntu server.
Now I want to place my Server between the router and the switch. This is because I want everyone to go through the proxy server to filter some web sites.


I am facing some difficulties in the configuration of the two NIC cards on the ubuntu server.
It has two interfaces em1 and em2 to which I want to assign static IP addressses. This is what I have configured so far:


##The primary network interface
auto em1
iface em1 inet static
address 192.168.1.30
netmask 255.255.255.0
gateway 192.168.1.2
network 192.168.1.0
broadcast 192.168.1.255


## The secondary network interface
auto em2
iface em2 inet static
address 192.168.1.31
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255


I read some posts that said there shouldn't be a gateway entry in the second interface so the OS knows which interface to use.


My current network architecture is the following:


FSI-->my CISCO Router (192.168.1.1) --> my Ubuntu server (containing two NIC cards and running squid proxy and iptables firewall)--->my switch--->some laptops


The problem is laptops are enable to connect to the internet. I don't understand why. I disabled the firewall and the proxy but I still cannot connect.


Should I configure some routing rules between the two NIC cards or should I use the FORWARD chain of iptables? How can I solve this?


Thank you for any help.

---

### Post by kpatz on 2015-01-07
Your two network interfaces need to be on different networks/subnet IP ranges.  So, for example, have em1 on 192.168.1.30 and em2 on 192.168.2.30.  Connect em1 to your router and em2 to the switch.  Give your laptops 192.168.2.xxx IPs (other than the server's IP).  Ideally, set up a DHCP server on the Ubuntu server to hand out IPs to the clients, then you don't have to set them up manually.

Then set up forwarding in your iptables rules using the FORWARD chain (unless you want to enforce that ALL traffic goes through the proxy, then just set up the proxy).

---

### Post by anis-bedhiafi on 2015-01-07
Thank you for your help. I configured the interfaces as follows:

# The primary network interface
auto em1
iface em1 inet static
    address 192.168.1.30
    netmask 255.255.255.0
    gateway 192.168.1.2
    network 192.168.1.0
    broadcast 192.168.1.255


# The secondary network interface
auto em2
iface em2 inet static
    address 192.168.2.30
    network 192.168.2.0
    netmask 255.255.255.0
    broadcast 192.168.2.255

and iptables as follows:
-P INPUT ACCEPT
-P FORWARD DROP
-P OUTPUT ACCEPT
-A FORWARD -i em1 -o em2 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i em2 -o em1 -j ACCEPT
-A FORWARD -j LOG

now when configuring my laptop, let's say i want to give it the IP 192.168.2.15 then which gateway should I specify? Should I use the server IP 192.168.2.30 as gateway ?

---

### Post by anis-bedhiafi on 2015-01-07
Thank you it worked. the gateway for the clients should be the em2 ip address of the server

---

### Post by kpatz on 2015-01-07
> **anis-bedhiafi said:**
> Thank you it worked. the gateway for the clients should be the em2 ip address of the serverCorrect.  em1's gateway should be the IP of the router; em2 doesn't need a gateway, and the machines connected to em2 would use em2's IP as the gateway.  That way the computers know how to route packets from themselves to the internet and back.

In fact, your server is acting as a router now; depending on what you're using for an internet connection and if nothing else is connected to the Cisco router (i.e. wireless clients), you may not need the Cisco at all anymore.  For a typical cable internet setup using NAT and DHCP it's easy to set up Ubuntu and iptables to do this.

If you install a DHCP server (such as isc-dhcp-server) you can have the clients get IP, gateway and DNS from the server instead of having to set up each client with its own IP, etc.

---

### Post by anis-bedhiafi on 2015-01-07
Actually I need that Cisco router because I am using fiber optic cable to the FSI. It works so fine now, thank you.

---

