---
title: "Help Routing Between Two Nics"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by FragglePete on 2007-05-08
Hi,

Hope you guys can help, I'm banging my head against the wall at the moment.

I'm a Windows guy at heart, but widening my horizons with Linux primarily for a project that won't allow me to use Windows due to licencing.  So, please be gentle with me!!! ;) 

I have a network which consists of two subets.  Each subnet has it's own Internet Connection and is managed by DHCP quite nicely using an IPCOP box for each Subnet for caching primarily.  Each subnet is an accomodation block (of sorts) with both having their own Internet Connection and I need to ensure that each subnet is using the correct connection.

I've added a third box, this time running Ubuntu Server which has two NICs in use, each one connected to each subet.  This box will be running as a LAMP server so we can run things like an internal web server, forums, etc.

Now, each subet can see the Ubuntu server no problems, but I want each subnet to be able to see each other,so esentially use the Ubuntu to route between each subnet.

I've been posting on the IPCOP forums, but help has dried up a bit at the moment, I've played around with add route stuff on each IPCOP box, had a go at enabling Port Forwarding, but I'm still struggling in being able to see other PC's on the other subnet.

Attached is a diagram of the current network setup.

I'd appreciate some step by step help in getting this to work.

Many thanks

Pete

---

