---
title: "RDesktop Help Computer Access Through Router From School"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by themayoradamwest on 2008-11-12
Hello. I am wondering how to access my Windows XP Computer (which is connected through a router) via Remote Desktop (RDesktop) from a location that is not within my network on my Ubuntu 8.04 Laptop. I would like to connect from school, for instance, but I know that entering the following won't get me anywhere since the IP is for a generic router and not an actual IP for a computer location that is unique:

rdesktop 192.168.1.100

Thus, I was wondering if you could tell me how to get through the router and to my actual computer that has another IP. Thank you:)

By the way, I can easily access my Windows Computer from my ubuntu one when I am connected to the local network, but it is only when I leave the network that I cannot. So, how do I tell my laptop to find the windows computer through the router and access it when I am not in the network? Thanks very much :)

---

### Post by superprash2003 on 2008-11-12
to avoid all pain, you could use logmein a free service [www.logmein.com](www.logmein.com) ..

---

### Post by jonobr on 2008-11-12
Hello


Depending on your network admin, you may be able to chat with them and let them know what your at, they may be able to help you.
They could (if they are helpful) provide very restrictive access to you alone.
You may end up in a world of hurt if you try to circumvent their network security and they find out.

---

### Post by themayoradamwest on 2008-11-12
Network Admin? Do you mean who controls the router? If so, then it is just me and my roommate.

---

### Post by jonobr on 2008-11-12
So assuming that your college allows remote desktop out, I think you will need to setup some kind of port forwarding on your router.
Usually in the config of your router it will allow you to forward based on a port number to a specifc machine.

The other thing you will have to watch for is if you get a dynamic IP address from your ISP rather then a static one, then you will need to do something like using a dynamic IP address mapping service like /www.no-ip.com to be able to connect to the most current IP address assigned to your router

---

### Post by jonobr on 2008-11-13
Hi

Looking at posts this morning, I notice someone has a resource online dealing with this topic, 

Here it is 
[http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

---

### Post by RMOP on 2008-11-25
Easier than you'd think.

1] Make sure your home router supports DynDNS

2] Go to DynDNS and get a free account.

3] Create a domain name with DynDNS

4] Register your home ROUTER with DynDNS

5] Setup a PPTP VPN server on your Windows machine. I used a SEPARATE account than ones used for normal login. I used a machine-generated strong PW and a machine-generated userid as well. That's the ONLY account allowed to connect to my XP machine over the VPN.

6] Setup a PPTP VPN client account on your Ubuntu machine. You'll need a home router that can pass GRE 47 protocol packets. Enable PPTP Pass-through is supposed to accomplish this, but it does NOT work on a number of routers.

7] Make sure you can connect from Ubuntu using VPN.

8] After connecting over your VPN, you should be able to run RDESKTOP as if you were on your home network. Because you will be, in effect.

There are LOTS of sites with a PPTP VPN howto for Windows, including ones to tell if your router at home is blocking GRE 47. Of course, your remote router has to allow PPTP outgoing, but in my experience, most do. Technically, you might be able do this w/o a VPN, using only DynDNS, but I would advise against it.

Good luck. This works great for me.

> **themayoradamwest said:**
> I was wondering if you could tell me how to get through the router and to my actual computer that has another IP. Thank you:)

---

