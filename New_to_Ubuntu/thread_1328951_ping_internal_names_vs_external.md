---
title: "ping internal names vs external"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by dlewis187 on 2009-11-16
Simple question
I have a windows machine called precision as in dell workstation
In Ubuntu 9.1 in terminal if I type
ping precision I get
precision.socal.rr.com (208.67.219.132)
Other internal addresses do not resolve correctly either
I am on a 192.168.0.x internal network.

In network connections > wireless ipv4 settings I have DHCP and I have tried DHCP address only and put in the routers address 192.168.0.1 for the DNS server
IPv6 is disabled.

---

### Post by dlewis187 on 2009-11-20
top

no one has an idea about this?
My windows machines work properly, why not ubuntu?

---

### Post by whitethorn on 2009-11-20
Does your windows pc have a static IP?  You might be able leave it with DHCP and give it a static IP on your router.  Then open /etc/hosts and add the IP and the hostname of your windows pc.  That's how I set it up, I don't have an internal DNS server.

---

### Post by lavinog on 2009-11-20
see if precision.local works (i don't have any windows machines to test this with, but I don't think it will work.)

see if **nmblookup precision** gives you an ip address

In the past I had to install winbind to resolve windows names.  Windows uses wins name resolution.

I started working on a script that can automatically keep your host file up to date for this reason.  It works by resolving the name to a mac address then getting the ip address from the mac address.  I can see if i can finish it if the winbind method doesn't work.

---

### Post by dlewis187 on 2009-11-20
I'm not sure what a static ip address will accomplish
Windows & ubuntu are getting dns from the router 192.168.0.1
The problem is that ubuntu is not getting internal addresses names.

---

### Post by lavinog on 2009-11-20
did you try winbind?
windows does not resolve local names with dns.

---

