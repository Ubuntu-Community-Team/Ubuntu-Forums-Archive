---
title: "nautilus display servers multiple network hops away"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by Kulgan on 2008-05-31
Hi!

My house contains two routers. One is a modem combination, the other a normal wireless router. My laptop is on the second router.

I have recently moved stuff around in my house, and the server, which used to be on the same router as me, ended up connected directly to the modem/router. This means that Nautilus no longer lists the shares in Places -> Networks. I have to go enter in smb://<ip> or smb://<hostname> in the navigation bar the first time. (There is an entry for it in /etc/hosts.) 

While I could make a launcher on the desktop, or add it as a network place, I liked it as it was. It was also prettier. The way it was meant to be. So before resorting to that, I would like to know if it is possible to get Nautilus to check the rest of the network as well - or just checking the server's IP. 

Thanks
-K

---

### Post by jetsam on 2008-05-31
It adds a lot of complexity to a network to manage two different subnets, and it isn't really possible to do properly with two consumer routers.  It can work, but it's hard to set up two way communication between the subnets.

A solution like this might work for you, which explains how to use the second router as a switch on the same subnet as the first router:
[http://www.smallnetbuilder.com/content/view/24431/53/1/2/]("http://www.smallnetbuilder.com/content/view/24431/53/1/2/")

That's page three of the article.  The whole article explains the problem pretty clearly, so you might want to also look at the rest of it.

---

### Post by Kulgan on 2008-05-31
Well, I would really like to keep the second router as a router. If that's not going to work I may as well replace it with a switch. I have an unused one any way. Alternatively, I could rewire the server to the second router (at the moment, it is connected to the first one via powerline adaptors), but that would require more doing that I was planning on doing. Which is why I hoped there might be some way to get Ubuntu to see the server directly. 

But if that's not the case, I'll have to find a better option. The article mentions port forwarding - perhaps that might help, perhaps not.. oh well. 

Thanks for the insight!
-K

---

### Post by jetsam on 2008-05-31
You know, it might work to just use **places-->connect to server** and fill in your server's ip address and other info.  What's tough to get working with two subnets is network browsing between the subnets.  

There are other solutions of varying complexity I've seen before but haven't personally tried ...  a wins server, vpn between the subnets, putting the laptop in the second router's "dmz".  Port forwarding could possibly be made to work as well.  I believe ports 139 and 445 are the two important ports for Samba.

I've been wrestling with the two subnet thing because I'd like to set up a test network which I can break at will and not affect the rest of the network.  It has turned out to be a bigger challenge than I thought it was.

---

### Post by Kulgan on 2008-06-01
Yeh, entering it manually works. Only the icon doesn't stay on after I unmount it, unless I add it as a "bookmark", which is not what I want. Clutter. This is an issue of getting Gnome to see the server on its own, not of actually connecting to it - which I take it is where the firewall in the second router could be causing problems (blocking the traffic that "informs" the laptop of the samba server's prescence?). Routing table on second router:
```
	Action	 Name	 Source	 Dest	 Protocol, Port	 
	Allow	SMB139	*, *	LAN, 192.168.0.101	TCP,139	
	Allow	SMB445	*, *	LAN, 192.168.0.101	TCP,445	
		DMZ Server	*, *	LAN, 192.168.0.101	*, *
```
Where 192.168.0.101 is the IP of my laptop.

I think the upgrades did funny things to that part of Gnome, and I'm planning a clean install in a while, so I'll see if that sorts anything.

Putting a wins server on the server and setting smb.conf to the server's IP doesn't seem to be helping. Neither is sticking it in the DMZ. When I have the time to do a fresh install, I will, and hope for the best. 

Thanks for the tips
-K

---

