---
title: "Exposing two LAN IPs to the internet"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by tycoonheart on 2007-11-07
Hey guys, I have a little dilemma.

I have a Dell PowerEdge Server.  One of the features of this server is the Remote Access Controller.  It lets you start/stop the server remotely using the web-based controller.  I have got the NIC for it set up locally for a static IP of 192.168.1.2.

I've got Ubuntu Server 7.10 installed on the server, and set up at IP 192.168.1.3.  I can access either of those from anywhere within my network no problem.

The LAN is behind a linksys router, and I set up a DYNDNS account to manage the IP.

Now, I'd like to to be able to access both the server and Dell's RAC from a remote location.

The router has DMZ functionality, but I can only forward it to one local IP.

Is there something I can do, like specify something like myDomain.com/RAC to get to the RAC server and myDomain.com/Server to get to my Ubuntu server?

Thanks for the help in advance.

---

### Post by Mithrilhall on 2007-11-07
I'm a little confused.

So your RAC is on 192.168.1.2 and the Server (OS) is setup on 192.168.1.3?

The Remote Access Card is web based on port 80?..and what are you trying to get to on the server itself?

---

### Post by tycoonheart on 2007-11-07
> **Mithrilhall said:**
> I'm a little confused.

So your RAC is on 192.168.1.2 and the Server (OS) is setup on 192.168.1.3?

The Remote Access Card is web based on port 80?..and what are you trying to get to on the server itself?

I've got a few things running on the server. I'd like to be able to SSH into it.  I've also got Sun Java App Server running on it, I'd like to be able to deploy some custom applications to it and view them.

Yes the Remote Access Controller is on port 80 on 192.168.1.2

Hope that cleared it up.

---

### Post by Mithrilhall on 2007-11-07
No need to use the DMZ. Just port forward 90 the 192.168.1.2 and the other ports you need open (22, etc) to 192.168.1.3.

---

