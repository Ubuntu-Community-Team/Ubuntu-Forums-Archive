---
title: "Ubuntu VM Appliance with Static IP"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by djMoralita on 2006-12-07
Hello everyone, 

I have just started using Ubuntu. I am trying to setup a VM Appliance using Ubuntu, and I need to keep a static IP intact for this VM Appliance so it could be ported in differenthosts with a static IP that is set within the application installed within Ubuntu. 

I've tried the following:

(1) Bridged Networking (DHCP). I got an server assigned IP which is visible thru the LAN, but I need a static IP so this won't work.

(2) NAT. I got a server assigned IP that is visible to the host computer, however, this IP changes when ported to a different machine. I need a static IP so this won't work either.
d
(3) I tried Bridge Networking (static-IP), I have a static IP, but this IP is not visible to the host computer. I don't know to link it automatically to the host computer, I manually configured /etc/network/interface, I'm missing the element of connecting the host machine to my ubuntu installation. 


I tried searching the forum for a similar case, but I'm not successful yet, hope I can get some help!

Thanks in advance,

DJ

---

### Post by djMoralita on 2006-12-07
I've figured out how this works, I was basically using the wrong IP class to connect to the LAN, but I also realised that this is not a full-proof solution to what I want to do. :)

---

