---
title: "VNC Remote Access from accross the internet"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by JohnnyWhite2007 on 2008-07-15
Hi,

I am trying to remote access my computer at home from work. I have about 5 computers running at home and I need to connect to just one. Through VNC on xp at work I type in the IP address i found from [www.whatismyip.com](www.whatismyip.com) for that computer at home, i noticed though that all the computers at home have the same IP address. I use a Linksys wireless Router to spread the internet accross to them. How do I connect to just one computer on my home network from my office computer using VNC? 

Is it possible to set seperate IP address to each computer?

---

### Post by PRMan on 2008-07-15
In your router, there are settings called "Port Forwarding".  Set the VNC port # to point to the internal IP address of the computer that you want to control. I don't know what the port # is off the top of my head, and you definitely want to change it to something non-standard over 255 and less than 65535.

If you want to control all your PCs, just make each one of them use a different VNC port number and then forward each of those numbers to a different (internal) IP address.

Then you could use VNC 123.45.67.89:Port#1 for the first one, VNC 123.45.67.89:Port#2 for the second one, and so on.

But may I mention that this is EXTREMELY DANGEROUS!  VNC is very easily hacked.  Your machine probably wouldn't last a day before giving someone else complete control.  Make sure you read up on how to make VNC secure.  Even then, there is a risk that your whole network may be compromised.

---

### Post by Leed on 2008-07-16
Check to see if your Router has a VPN functionality, I'm also using a Linksys  that supports this. That way you could connect to the network and access any of the 5 pcs using their local ip addresses. Also a VPN tunnel is much more secure than simply connecting to your home network (a very bad idea). 

if you consider on buying a router with vpn, I'd suggest not to get another linksys, they are unfinished crapy items and you'll have problems getting support from linksys. The firmwares on the site are not up to date, and the unreleased betas have bugs and are hard to get. 

The ports you should use for VNC are 5800 or 5900, you may need to open these ports on the pc firewall if you are using one. 

you can set up most routers to a fixed internet address by registering one on [www.dyndns.org](www.dyndns.org) and setting it up on your router.

---

### Post by crtlbreak on 2008-07-16
> **PRMan said:**
>  ..... that this is EXTREMELY DANGEROUS!  VNC is very easily hacked.  Your machine probably wouldn't last a day  .... 

Agreed
There are serious security intrusion risks with open VNC connections so the best way around that is to limit the source of the vnc traffic (your office probably has a fixed range?) to a range of IP addresses. That way your router/firewall at home will only allow access from a limited fixed range (or even dymanic if the dyndns option is used.

> **Leed said:**
>  .....  Also a VPN tunnel is much more secure than simply connecting to your home network (a very bad idea). 

agreed - there is also vnc over ssh - quite complex to set up but bulletproof once done.

> **Leed said:**
>  The ports you should use for VNC are 5800 or 5900, you may need to open these ports on the pc firewall if you are using one. 

I recommend not using default ports for VNC - first set it up with defaults to get it working - then change the port numbers (as everyone knows vnc/tightvnc exists on :5900) - and then remap those new ports within your firewall (if it offers port re-mapping?) to internal addresses - only from a fixed source range.

regards

---

