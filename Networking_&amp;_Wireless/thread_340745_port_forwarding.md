---
title: "port forwarding"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by Sterkarm on 2007-01-17
Right, well im an absolute beginner realy at this, and iv been reading through many forums and post to work out how to do this, but keep meting confused.... 

What i want to know is how to access my computer and files on a private ip  through the public ip address, or even just how to get it.  Their are a number of different computers on my lan, the nat thing being on my brothers, which i can access over the Internet with the public ip address... but i want to know how to get my computer as well. 

I would like a step by step guide if possible please, as my brain cant take too much, and i currently am getting lost on this. 

i only know my public and private ip address,  along with the port, do i need any more than that ? and what do i do with it in order to connect? 

matt

---

### Post by LotsOfPhil on 2007-01-17
It will depend on your NAT. Is your brother's computer doing the NAT, or is it a router?

---

### Post by goodfella on 2007-01-17
Do you know how to access your router configurations?

---

### Post by kipeloff on 2007-01-18
NAT rules should be applied to the router, which provides access to the public network for home network.
You have to translate another port to local PC, if the same application is used for PC remote access, as well you can change default used application 'port number', then forward it using NAT.
If you have Ubuntu as router, here is some guide about NAT configuration,
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

