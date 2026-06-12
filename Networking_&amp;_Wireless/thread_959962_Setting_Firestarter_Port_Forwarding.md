---
title: "Setting Firestarter Port Forwarding"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by rasurop on 2008-10-26
Help please....

Have the Linux/Ubuntu Ultimate Edition setup and have problem with port forwarding using Firestarter. Setup is listed below;

internet --> 
 router --> 
 Ubuntu PC (Firestarter); static IP 210.xx.xx.xx local 192.168.0.1 -->
 LAN/hub --> 
 Windows PC IIS/port 80 local 192.168.0.80 (and other local networks)

I manage to install Firestarter (firewall) from my Ubuntu Ultimate Edition and had internet connection sharing with it. So far, "all" workstations from the local network could now access internet (even the Windows IIS). Every LAN/network could ping each other and the Firestarter is detecting these activities.

Setup the Firestarter "Inbound traffic policy" forward service;
 HTTP port 80 --> 192.168.0.80 port 80

My web server resides in 192.168.0.80 IIS/Windows and I want to access this website from the outside world. Tried the Firestarter port forwarding instructions already but it is not working yet.

Question: how can I port forward my Firestarter HTTP service to access 192.168.0.80 IIS Windows server?

Please help....

---

### Post by cariboo on 2008-10-27
Give [canyouseeme]("http://www.canyouseeme.org/") a try, this will check if your isp is blocking port 80 or any other useful ports.

Jim

---

### Post by rasurop on 2008-10-27
Thanks for replying cariboo907.

Yes, tried it and the reply is;

Success: I can see your service on 210.xxx.xx.xx on port (80)
Your ISP is not blocking port 80


Tried this from;
1.  Ubuntu Ultimate (with Firestarter)
2.  Windows/IIS 192.168.0.80  (LAN)
3.  My laptop 192.168.0.102  (LAN)

They all have the same result. Still has problem; when I type [www.mydomain.com](www.mydomain.com) in my browser, the display is still


Failed to Connect

Firefox can't establish a connection to the server at [www.mydomain.com](www.mydomain.com)


Any other suggestions?

---

### Post by brodi6 on 2009-01-18
Not sure if anyone ever answered your question sufficiently. I ran a webserver from my home at one time too.  I never had any luck accessing it via the domain name from inside my home network. I always had to enter the internal IP address.  Have you tried accessing it via your domain name from outside your home?

---

