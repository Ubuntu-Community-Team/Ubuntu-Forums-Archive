---
title: "Network design: Where does the DHCP server need to be?"
date: 2017-08-13
forum: Networking &amp; Wireless
---

### Post by webmiester on 2017-08-13
Hi Everyone,

I am trying to design/redesign our current network setup.  I think that Ubuntu can be used as a DHCP server...  Now my question is, where does the server need to be located in order for it to work as a DHCP server?

Here is my current setup

ISP fiber optic connection  ---> Fiber Optic Media Converter  ---> Load Balancer (With DHCP function) ---> Main Switch (to multiple computers) ---->  secondary switch ---- > application server (Ubuntu server)

Now my point here is that I want to get rid of the load balancer and transfer it somewhere else...  I want to give the application server the DHCP function. Will this work? or will it only work for the computers connected on its secondary switch and below?  Should I attach the DHCP server as a computer on the main switch, or does it have to be connected BEFORE the main switch much like where the load balancer is placed (in which case it will need 2 LAN ports).  Thanks so much.

I was thinking of putting a firewall computer in place of the load balancer.  In that case, I can have that firewall function as a DHCP server too.  I went through the available free firewalls in ubuntu, but I think pfsense has the features I need.  I was reading about the DCHP function of pfsense and it says something like it only works to give static DHCP instead of dynamic DHCPs...  But I want dynamic DHCP.  So if ever I cant get pfsense to do the DHCP server functions properly, I was contemplating on using this setup I proposed where the application server I have will be the one to give the DHCP addresses.  Now you might ask why is it on a secondary switch?  It has something to do with their physical locations in the building.

Just in case anyone here is also familiar with pfsense (although I know this is the ubuntuforums), I would appreciate inputs very much.  The features I found in pfsense which I couldnt find together in a single firewall for ubuntu free versions are 1) Traffic shaping, and 2) Captive Portal.

Thanks so much,

webmiester

---

### Post by SeijiSensei on 2017-08-13
DHCP relies on broadcasts so the server must be on the same physical segment as the machines it serves.  In the past when I built Linux-based routers, we'd have DHCP listening on the internal-facing interface.

There are tools to pass DHCP requests through intermediate routers.  Look for articles about "DHCP relay" if you need that ability as well.

---

### Post by webmiester on 2017-08-19
Thank you Seiji,  I will look up your suggestion.

---

