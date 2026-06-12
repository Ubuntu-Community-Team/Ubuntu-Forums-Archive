---
title: "Trying to run a web server through WRT54G router"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by Spreadsheet on 2008-11-28
Ok I've asked in a lot of places but nothing ever worked...
I have Ubuntu and I'm running Apache, what I'm trying to do is so someone from the Internet can go to my IP address and then it forwards to the website. The server computer's local IP is 192.168.1.101 . What should I do?

---

### Post by redhotfire on 2008-11-28
> **Spreadsheet said:**
> Ok I've asked in a lot of places but nothing ever worked...
I have Ubuntu and I'm running Apache, what I'm trying to do is so someone from the Internet can go to my IP address and then it forwards to the website. The server computer's local IP is 192.168.1.101 . What should I do?

Try port forwarding in the router. Set the port and Ip address and you will be fine.

---

### Post by Spreadsheet on 2008-11-28
Yeah, but I have tried this. On the Applications & Gaming I have for Application, http, Start and End 80, protocol both, and IP Address 192.168.1.101. I also enabled it.

---

### Post by kevdog on 2008-11-28
First of all, have you tested your apache setup from within the lan??  Just to make sure that the web server is up and running.  It should be as simple as port forwarding on the router, unless you have activated the firewall on the router or on the server itself.  You could always post 
iptables -L
to see the server's firewall.

---

### Post by gpsmikey on 2008-11-28
A number of ISP's block port 80 traffic to their clients - they don't want you running web servers (and tell you so in their AUP).  You may find that your ISP is blocking incoming port 80 traffic - if that is the case, nothing you do to your router will give access to someone outside.

mikey

---

### Post by linuxisevolution on 2008-11-28
> **Spreadsheet said:**
> Ok I've asked in a lot of places but nothing ever worked...
I have Ubuntu and I'm running Apache, what I'm trying to do is so someone from the Internet can go to my IP address and then it forwards to the website. The server computer's local IP is 192.168.1.101 . What should I do?

Try this: [http://71.206.223.52/apache2-default/linforum/forum/forum/index.php?view=topic&board=12&top=1]("http://71.206.223.52/apache2-default/linforum/forum/forum/index.php?view=topic&board=12&top=1")

Also, you must enable dmz in your router.

---

### Post by Cheap Webcam on 2008-11-28
Dear:[**cheap webcam**](http://www.agoodic.com/viewproduct.asp?/PC_webcam_24bit.htm) in agoodic.com&#65281;Using your [**webcam**](http://www.agoodic.com/viewproduct.asp?/PC_webcam_24bit.htm) all right? [Agoodic](http://www.agoodic.com/viewproduct.asp?/PC_webcam_24bit.htm) to be compared. And very cheap. Just do it now.

---

### Post by J172 on 2008-11-29
With the WRT54G (v5.x anyways) DMZ isn't required. What can do is enable DynDNS which is accessible under the DDNS settings (I *just* got a new router, I think its under Administration). Grab a free DynDNS.com account (at that site) and input the details. However, your port settings need to still be enabled and correct/working for this to work. So you could access your server at [http://geek1.selfip.net](http://geek1.selfip.net). Also if you do port forwarding and forward an external port XXX to internal port 80 (same IP), you could bypass the AUP (or change from port 80 to port XXX by changing the Apache configuration file's ListeningPort line). [COLOR="Teal"]**HOWEVER, AUP's are generally legally binding, hence this would be illegal. Check with your ISP. If they don't allow it, you can be asking for trouble.**[/COLOR].

Also note, that with the WRT54G (again v5.x anyways) even with the newest firmware, the DHCP lease is 24 hours default and there is no DHCP Reservations. So if your webserver computer is off the network for 24+ hours, it *might* get a different IP Address. Make sure your webserver conf is on 127.0.0.1 so it pulls what ever the NIC ip is. And also that your port configuration is correct for any new IP it gets, on the router.

---

