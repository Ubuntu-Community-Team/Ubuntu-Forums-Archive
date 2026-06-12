---
title: "Server and Router have same public IP address"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by corevette on 2010-03-18
I have a Router on the network and an ubuntu server on the network with the same public IP address (but different local IP's).  This isn't a problem except the server has Apache installed and when I try to access the server via the public IP address, it takes me to the router web interface.  What can I do to get around this?  There doesn't seem to be an option to change the port of the web interface (it's a cisco rvl200).  Any ideas?
Thanks

---

### Post by halitech on 2010-03-18
how did you manage to get 2 machines to work on the internet with the same public IP address?

---

### Post by corevette on 2010-03-18
The router has a static IP address, so maybe everything in the network has a static/same public IP address?  It would be very nice if we could change the port for the router, but I don't think it is possible :-(

---

### Post by halitech on 2010-03-18
only 1 device can have a public IP address otherwise nothing would work properly and traffic would be directed to computers where it wasn't desired. How do you have things set up? ie. is the server connected to the router?

---

### Post by corevette on 2010-03-18
cable from wall --> modem --> vpn/router (with a static ip) --> dhcp server --> switches --> computers

---

### Post by halitech on 2010-03-18
looking at the way you describe it, all the computers will have the same public IP address but different internal IPs.

I normally point people to [http://portforward.com/routers.htm](http://portforward.com/routers.htm) for setup info but doesn't seem to have your router listed. I would suggest contacting Cisco and see if they can help (if you can't find the manual)

---

### Post by cerealtx on 2010-03-18
you need to setup port forwarding in your router IOS, also, to stop it from loggin into the firmware of the router, turn off remote connection, also u can change the port on most Cisco IOS to change the remote login

---

### Post by eronisko on 2010-03-18
Your router's manual (in case you don't have it):
[http://72.163.4.161/en/US/docs/routers/csbr/rvl200/administration/guide/RVL200_V10_UG_C_WEB.pdf]("http://72.163.4.161/en/US/docs/routers/csbr/rvl200/administration/guide/RVL200_V10_UG_C_WEB.pdf")

On page 14 (Setup Tab > Forwading) you will find guidelines on how to set up port forwading to your machine from outside.

:!: **However**, note that exposing your computer to the public might be a great security risk.

---

### Post by corevette on 2010-03-18
What does port forwarding have to do with my problem? The reason I can't access the webserver is because both the webserver and router web interface use port 80. Yes each computer has a different ip address internally, not from outside the network.  I don't seem to be able to change the port of the router interface.

---

### Post by Iowan on 2010-03-18
Unless you REALLY need to configure the router from externally, it should work as intended to forward port 80 from the external router port (public IP address) to the internal server address. If your ISP provides dynamic address, you may need a service like [dyndns.com]("http://www.dyndns.com/") or [no-ip.com]("http://www.no-ip.com/").

---

### Post by halitech on 2010-03-19
> **corevette said:**
> What does port forwarding have to do with my problem? The reason I can't access the webserver is because both the webserver and router web interface use port 80. Yes each computer has a different ip address internally, not from outside the network.  I don't seem to be able to change the port of the router interface.

Port forwarding has everything to do with your issue. Web browser traffic travels by default on Port 80 unless you tell it otherwise. 

[http://portforward.com/help/portforwarding.htm](http://portforward.com/help/portforwarding.htm)

What you need to do is tell the router that incoming traffic on Port 80 is to be directed to your internal IP address of your server (ie 192.168.1.101) so that the "outside" world can see the server. If the router does not have the option of turning off the remote access and port forwarding then you will need to either get a different router or set your server as a DHCP server and have the internal computers get their IP address from it and remove the router from the setup.

---

### Post by fela on 2010-03-19
OK so this is how I understand it:

your router is running a DHCP server with the server behind it, so to the outside they appear to be the same machine (ie. it can't see the server).

You need to forward port 80 (assuming you haven't changed apache's default port to something else) to the server using the router's web interface. If it doesn't support that, I'm afraid I think you're scr*wed, and need a new router that supports port forwarding.

Edit: seems like halitech seems to agree with me :)

---

### Post by eronisko on 2010-03-19
1) As Iowan said, unless you really need it, disable the Remote Management feature (Firewall -> General)
2) Set port forwarding from outside to port 80 to your webserver.

When you send out a request to your external address on port 80, router will initially respond with *its own* service running on this port. In your current case, that would be the managing/administration interface  - which is very insecure, btw.
When you set-up port forwarding, you tell the router to *relay* each port 80 request to your web server. In other words, if someone from outside asks your router for a website, it will redirect them to your own webserver.

---

