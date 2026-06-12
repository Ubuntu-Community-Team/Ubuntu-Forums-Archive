---
title: "Another Noob in search of help!"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by ReSInX on 2011-03-20
Hello everyone! I have plans to set up a few websites for the community children support programs where I live. Hope to open a small drop in center/Internet Cafe in the near future but I better learn what I am doing fist!
 
What I HAVE right now!
 
Static IP (Just got it today)
Ubuntu Server 10.10
[Acer Altos G530 Server]("http://reviews.cnet.com/soho-servers/acer-altos-g530-xeon/1707-3125_7-32336503.html#manDesc")
- 3.2Ghz Xeon Processor
- 4 gb ECC DDR2-400
- 3 X 100GB Seagate SCSI HDD 10k RPM
- Raid Control 
- Dual NIC's
[D-Link WBR-2310 Wireless Router]("http://www.dlink.ca/products/?pid=470")
5 Windows 7 Ultimate Workstations
1 Windows xp Home laptop
 
What I NEED to setup
 
Now I have to figure how to host and supply internet service to the other computers in my home! Should I assign my Static IP to my Router or my Server? IP is bound to the MAC address of NIC1 in my server but masquaded on the router right now. Server does not have Internet Access because of IP conflict. How do I have my server send the Internet to my router? I guess what I am asking is how would you do it? :confused:

---

### Post by Vaphell on 2011-03-20
Your static IP should go to your router (with the MAC spoofing as IP is bound to a different physical device - just like you did). Your computers inside LAN and server in particular should be given a local network IP (for example 192.168.x.x). While your 'normal' computers don't require fixed IP and can use autoassigned IPs given by the router (which can be different at different times), your server has to have fixed IP - it's necessary for port forwarding. If your router is fancy and allows for setting fixed IP for a given MAC address in its DHCP feature, cool - if not, you have to configure IP manually on your server. Additionally your router should forward necessary http ports to allow direct traffic to the web server's IP so the machine can be reached from outside.

---

### Post by mapes12 on 2011-03-20
Try this:-

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

Your post title needs to be more specific, like "How to set up a small web service?"

And Google is you friend.

Good luck with your project and welcome to Ubu.

Mark

---

