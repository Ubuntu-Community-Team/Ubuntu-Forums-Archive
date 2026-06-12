---
title: "VPN basic questions (OS independent)"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Mariano Oliveto on 2008-08-15
This isn't an Ubuntu nor GNU/Linux specific question but I guessed you might be able to help. If I'm too offtopic or in the wrong Forum please forgive me.

First I'll describe the situation:

Network "A" has 13 computers all connected with a switch and they all have Internet connection. One computer has a VPN Server installed.

Network "B" has 4 computers, it is, lets say, 20 kilometers away and also has Internet conection. One of the computers has a VPN client installed and can connect successfully to Network "A", browse the shared folders and printers, transfer files, etc.

These are my questions:

1) Can a PC from network "A" browse network "B"'s shares and printers?

2) Can I add a shared printer of the VPN client PC of network "B" in a PC of network "A" so the PC from network "A" can print to the printer that is 20 kilometers away?

I guess that if I set up another pair of VPN Server/Client but the other way around (server in "B" and client in "A") I could manage to do this but I wouldn't like to do this if I can solve the problems with my actual config.

By the way... all PCs in both networks are running MS Windows... I still posted here because I guessed this is still a basic networking question. If I'm wrong, please forgive me.

---

### Post by Mariano Oliveto on 2008-09-03
Well, since no one answered the post I'll just post what I found out so far:

> 1) Can a PC from network "A" browse network "B"'s shares and printers?

Apparently yes (althought I haven't been able to do it so far)

> 2) Can I add a shared printer of the VPN client PC of network "B" in a PC of network "A" so the PC from network "A" can print to the printer that is 20 kilometers away?

Apparently yes (althought I haven't been able to do it so far) :P As far as I can see, the problem might be with the router/firewall configuration.

I'll keep on working on it (in my little spare time) and post if I have any luck.

---

### Post by usererror on 2008-09-03
To answer your questions, yes.  I have no idea what this VPN software/client you are using, but you may want to check out "IPCop"

I use it at home and setup VPN connections between myself and sites I remotely support.

what kind of routers are you using at the sites?

Check out their website: [http://www.ipcop.org/](http://www.ipcop.org/)

---

### Post by NadmanET on 2008-09-03
Yes that does all sound possible.  That's what VPNs are really for; allowing remote access to resources which have their protocols blocked at the firewall/router.  (There are many other uses, this is just the most common.)  I have had problems seeing iTunes shares over a VPN but I really haven't had time to research how that protocol works.

I've never configured a Windows box as a VPN termination point so I can't really give you any steps for setting it up that way.  If there is a need to have a constant connection between the networks you should get the right gear in place.  If I were you I would get a couple Cisco ASA 5505s and set up a point to point VPN connection and turn on split tunneling.  That would be the ideal solution but if there is no budget or if you want to work with what you have I would use a Linux based OS.  I say that because I assume that the Linux software will have more features and will be more reliable as a VPN concentrator.  I could be completely off on that but I just don't hear of many people terminating VPNs on a Windows server.

If you don't need a constant connection between network A and B you could set up a client to site VPN.  Configure every host with the VPN connection info and when you want to access a resource on the other network, you could connect, get what you need, and disconnect.  The problem with this setup is that it is more labor intensive.  Your users will have to know where the resource they need is and understand VPNs enough to know when to establish the connection.  Also you would have to have a VPN server on each network.  

I should clarify that while I'm using the terms "client to site" and "site to site" there is always a client/server relationship when establishing a VPN connection, even in a site to site setup.

Unfortunately you are probably in the wrong place to get help with troubleshooting your Windows application.  Good luck and let me know how it goes.

---

