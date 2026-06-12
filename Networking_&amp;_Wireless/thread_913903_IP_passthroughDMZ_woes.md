---
title: "IP passthrough/DMZ woes"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by unityofsaints on 2008-09-08
Hi,

I'm in the process of configuring my headless storage server. I need SSH, deluge webui and webmin access from outside so I've put it in the DMZ of my router (Netopia 2247-NWG). I've been able to access it from outside via my public IP fairly reliably but as soon as I restart the router and the IP changes (I have dynamic IP) I can't connect with SSH anymore and pings time out, even though ifconfig will show the new IP.

All the relavant ports are open, but I wonder if there is anything I should configure in the box itself to make this DMZ business more reliable? Sofar I've only enabled the DMZ for the server in the router and then checked ifconfig to see if the IP has been passed through.

The server is running Ubuntu 8.04.1 Server Edition btw.

Any thoughts/suggestions?

Many thanks in advance :)

---

### Post by aago1254 on 2009-06-27
> **unityofsaints said:**
> Hi,
 
I'm in the process of configuring my headless storage server. I need SSH, deluge webui and webmin access from outside so I've put it in the DMZ of my router (Netopia 2247-NWG). I've been able to access it from outside via my public IP fairly reliably but as soon as I restart the router and the IP changes (I have dynamic IP) I can't connect with SSH anymore and pings time out, even though ifconfig will show the new IP.
 
All the relavant ports are open, but I wonder if there is anything I should configure in the box itself to make this DMZ business more reliable? Sofar I've only enabled the DMZ for the server in the router and then checked ifconfig to see if the IP has been passed through.
 
The server is running Ubuntu 8.04.1 Server Edition btw.
 
Any thoughts/suggestions?
 
Many thanks in advance :)
 
 
hello have you changed your internal server to 8080 this will make the web traffic travel on this and then you can do the ippassthru 
 
go to configure then adv then internal servers >   change the port 80 to 8080

---

### Post by aago1254 on 2009-06-27
also static your server and this will help it from changing there is no way to change keep the same ip in the modem you will have to static the server.

---

### Post by tgalati4 on 2009-06-27
I wouldn't run a server in the dmz unless you have run out of ports in your router and dmz is hard-wired. 

It's better to put it behind the firewall and port-forward only those ports that you need open.  There are several posts in the forums for ways to improve server security.

---

### Post by aago1254 on 2009-07-05
ture if you ip passthrough this modem all other computer connected will not work online.   :lolflag:  and that wouldnt be fun would it. ok if you need to open port 80 you need to go into the internal server and change the internal server http server to 8080 this way you can have what ever opened on 8080 on another lane so you can open those ports. and all that good stuff.  so open your pinholes under configure and make sure its the right type udp and tcp if you dont know open both and if you under configure and advanced as welll internal server is there .   good luck

---

