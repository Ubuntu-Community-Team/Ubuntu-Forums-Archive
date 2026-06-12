---
title: "Port forwarding"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Bromberj on 2010-02-03
I need to set up a remote desktop possible by port forwarding.  the second computer is on a different network, though a vpn can be set up, and information coming back to the main computer has to get through a firewall.  if anyone can give me a detailed step by step process on how to do this it would be much appreciated.

---

### Post by cariboo on 2010-02-05
There are a lot of different routers out there, you have to get into the router management interface, and set which port you would like to forward from which computer. If you are going to be doing this on a regular basis, It would a good idea to set up a static ip address.

---

### Post by drzoo2 on 2010-02-05
> **cariboo907 said:**
> There are a lot of different routers out there, you have to get into the router management interface, and set which port you would like to forward from which computer. If you are going to be doing this on a regular basis, It would a good idea to set up a static ip address.

My WTR54G Linksys router has a tab under security for VPN. I think this needs to be enabled on top of port forwarding but I'm not sure. I tunneled all my VPN traffic through ssh when I was using it. 

Port forwarding is easy. Think of it this way. When your request hits the router it needs to know what ports are being used by the VPN software, so these need to be opened. Then it needs to know where to route the packets so the IP address of the computer your connecting to needs to be added.

Depending on what VPN software you use may require different ports. Not sure. Google what your using to find out.

z

---

### Post by adam814 on 2010-02-05
[http://portforward.com/](http://portforward.com/)
They have guides for a lot of routers.

I wouldn't complicate it any more than it needs to be.  I tunnel VNC over SSH to do just what it sounds like you're doing.  The beauty of it is you can find clients/servers for both protocols for just about any platform.  That probably won't be the case with using VPN software.

---

