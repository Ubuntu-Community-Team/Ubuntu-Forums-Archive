---
title: "Ubuntu desktop as a webpage server"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by cearlp on 2008-10-05
I have two machines direct connected to a router, one runs ubuntu (8.04) and the other is a Mac.
The ubuntu machine is a LAMP, i.e., Linux, Apache, MySql and PHP installed. I can access the web pages I wrote on the ubuntu machine from the Mac but I can't access them from a machine that is attempting to connect from the net. I address the ubuntu machine by it's static IP address from the Mac but get no response if I try the same thing from some other computer.
So my questions are: 
Are there any configuration parameters somewhere that need to be changed? 
Is there other software that needs to be installed for my desktop to act as a server?
Is there something my ISP would have to do to facilitate my IP address being recognized external to my router?
Any help or suggestions will be appreciated.

---

### Post by jpkotta on 2008-10-05
You need to set the router to forward port 80 to the Linux machine.  Then you need to set up a dynamic dns service.  I use no-ip.com, but there are many (free) dynamic dns services.

---

### Post by cearlp on 2008-10-06
Thanks jpkotta for the info. It really helps.
Now, if I set the router to forward port 80 to the Linux machine  does that mean all traffic goes to that machine? If so, how does the other machine on the router receive anything?
The dynamic dns service just maps a domain name to an ip address doesn't it? I wouldn't need that service if I just use the ip address in the url, right?   (I realize that wouldn't be logical in a real world situation.)

---

### Post by superprash2003 on 2008-10-06
no, when you do the port forwarding.. only OUTGOING port 80 traffic would go from your linux machine.. so the other machine would have the normal internet access..Hopefully you know how to port forward..
 You could use no ip incase you dont have a static ip.. so you can get a free domain name like myname.no-ip.org or myname.sytes.net etc.. and then whenever you try to access the free domain name link, it would point to your computer..
Here's how you setup no ip on ubuntu [http://prash-babu.blogspot.com/2008/05/how-to-setup-no-ip-on-your-computer.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-no-ip-on-your-computer.html)

---

### Post by jpkotta on 2008-10-06
Port forwarding doesn't affect outgoing (from your LAN) traffic.  Any inbound (from the internet) traffic on port 80 will get routed to the Linux machine.  Note that the client is the only thing that sends out packets on port 80.  When you get data from a web server, it listens for requests on port 80, but sends replies on a different port ([http://en.wikipedia.org/wiki/Ephemeral_port](http://en.wikipedia.org/wiki/Ephemeral_port)).

You are correct about dynamic dns.

---

### Post by cearlp on 2008-10-07
jpkotta, Again thanks for the info, it's getting clearer but I'm still a bit confused. You say inbound traffic on port 80 gets routed to the Linux box but you say 'When you get data from a web server, it listens for requests on port 80, but sends replies on a different port.' My confusion is this: Port 80 is used by Apache (as I understand it) so  will forwarding port 80 to go specifically to the Linux box mean any data coming to the other PC on my router (who also might be running Apache) would go to the Linux box and not the other PC? 
I guess what I am saying is that both machines connected to my router interact with the internet and  I would like to be able to query both machines from the internet by simply addressing them by a specific ip address. My router seems to give each machine the same ip address whenever I boot them, no matter which machine is started first, even though the router config says they are assigned dynamically.

---

### Post by Iowan on 2008-10-07
> **cearlp said:**
> jpkotta,
I guess what I am saying is that both machines connected to my router interact with the internet and  I would like to be able to query both machines from the internet by simply addressing them by a specific ip address. If you have two separate machines behind the router, one of them must be adjusted to use an alternate port.  If you set the second machine to listen on port 81, you can forward port 81 to that machine.  (Might even be possible to forward port 81 on the router to port 80 on the server).

---

### Post by jpkotta on 2008-10-08
> **cearlp said:**
> My confusion is this: Port 80 is used by Apache (as I understand it) so  will forwarding port 80 to go specifically to the Linux box mean any data coming to the other PC on my router (who also might be running Apache) would go to the Linux box and not the other PC? 

Yes.  But only if it is using port 80.  As I said before, your browser sends out packets on port 80, but the server replies on a different port (which is actually guaranteed not to be port 80).  The only thing that will not work on your Mac is a server that listens on port 80 (and why would you need one - you have a Linux webserver).

> **cearlp said:**
> I guess what I am saying is that both machines connected to my router interact with the internet and  I would like to be able to query both machines from the internet by simply addressing them by a specific ip address. My router seems to give each machine the same ip address whenever I boot them, no matter which machine is started first, even though the router config says they are assigned dynamically.

Then you will have to forward a different port for the Mac.  For example, I run an ssh server on both my fileserver and my desktop.  I must forward different ports to each.  To specify a different port in a browser, add a :port to the URL.
```
http://www.example.com:8080 # browse to a webserver listening on port 8080
http://www.example.com:80 # redundant because 80 is the default
```

---

