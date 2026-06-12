---
title: "Intrepid server and DNS"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-01-16
I just read a guide for Intrepid server setup, here: [http://www.howtoforge.com/perfect-server-ubuntu-8.10-p4](http://www.howtoforge.com/perfect-server-ubuntu-8.10-p4)
That part made me wonder...If I set up the server as the guide suggests, I do not have to bother going to say, a site giving free dns service, as I can make my own static ip with the server?  And there was an option in the setup to use `DHCP`.  Though I`ve read on it, I still don`t fully understand DHCP.  It sounds like some computers have it and some don`t (not sure how to tell if mine does) but it is a good thing to have or choose in the setup, as it helps with serving, somehow? Still muddlud, please help `unmuddle` lol. thanks.

---

### Post by Vantrax on 2009-01-16
there are free services like dyndns that prevent that issue from being a problem externally. If its a home server for your own use internally then you dont need to worry about your external facing DNS and you can manually specify an IP.

---

### Post by hyper_ch on 2009-01-16
it is advised to use a static ip address if you want to operate a server - however it means a public static IP address so your ISP will have to provide you one (and normally they charge for it).

There are other services (dnydns.org / no-ip.com ) which will update your dynamic ip to a subdomain you can creat there (e.g. lakeside5.dyndns.org ). Depending on what router you have, you can setup a dyndns service directly in there.

A third option would be to buy a domain name and then and host its dns on [http://www.everydns.net](http://www.everydns.net) --> free service. They also have tools that you can then run to update the dns accordingly. I currently have a setup like this at my place and I make an update request every hour. It's a cron that runs on the server.

---

### Post by Lakeside5 on 2009-01-16
Ah, ok thanks guys I think I am clear now.  So when they talk about choosing this option when setting up the server, it would be in conjunction with paying the ISP for a static ip,  they don`t mean I can create my own static IP, gotcha.  I could buy a domain name and then get free webhosting, but I want to try my hand at hosting my own website (even though I seem to be AWFUL at it right now, maybe I`m a bit slow but stubborn, will get this eventually lol). I have really been thinking about buying a domain name anyway, And then I would use DYNdns to make it static.  quote: Depending on what router you have, you can setup a dyndns service directly in there.  I got a Dyndns account,  and put the username and password from that account into my router, as well as choosing the DynDns on the DNS page of my router, but beyond there I am confused as to: how to ftp my site up to there, I assume it would be  Basswebs.selfip.net? for host name in router, and also in the ftp connection (I use fireFtp) ?
I got a localhost to work (for developing websites within my computer) but not that.

---

### Post by hyper_ch on 2009-01-16
well, you have to differentiate between two IPs

Public IP : this one is assigned by your ISP and normally it is not a static IP
Internal IP: If you want to run multiple computers on a network with 1 outgoing ip you will require a router. So in order for the server to connect to the router you can assign there a static IP and then (for webhosting) you will have to forward port 80 from the router to your static internal server IP.

However, as you public IP changes because of it being dynamic, you will have multiple options:
- make your ISP to assign you a static IP (this might cost...)
- keep telling everybody you know what you current IP address is (tedious)
- use a dyn ip server like  noip.com or dyndns.org (both free)
  --> however if you have a registered domain (you can get one like for USD 9.99 or cheaper per year), then do not use noip.com or dyndns.org but rather use [http://www.everydns.org](http://www.everydns.org).

---

### Post by Lakeside5 on 2009-01-16
I know I am not going to have multiple computers hooked up to this network. Currently, it is just my daughter`s computer that shares the router with me (shared internet access). quote; So in order for the server to connect to the router you can assign there a static IP and then (for webhosting) you will have to forward port 80 from the router to your static internal server IP.`end quote
So, I am planning to get a paid domain name, and use my router, how do I assign the static ip for the router? and forward port 80 from the router to the internal server IP?
Also, thanks for the link Hyper_ch (I changed the end to .net, as .org was an image, not the website ;) )

---

