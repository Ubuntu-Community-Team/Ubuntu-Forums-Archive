---
title: "Server connection issues"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Jjjakal on 2009-03-31
I've been trying to get a server running, partly for experience and partly for a friend, and I've hit what I hope is a final problem.

I've got the server set up and the files I want in place, and I can get to my server just fine through any networked computer (By accessing 192.168.1.2, if it becomes relevant later).  My problem occurs when I try to get to my site from other networks.  When I access either the IP or the DNS from any network other than my own, I receive an error saying that "The connection to the server was reset", and the page cannot load.  In IE, instead of receiving the error, it just forwards to a google query of the URL.

I have set 192.168.1.2 as the DMZ host on my router, and I also port forwarded ports 22 and 80 UDP and TCP just in case.  What could be causing this error when trying to access the server?  How might I fix it?

---

### Post by HermanAB on 2009-03-31
Well, 192.168.x.y is a non-routable address and is good for LAN use.  To connect to the machine from elsewhere, you need to use the WAN address of your internet router, or if the machine is plugged directly into the internet modem, the address assigned by your ISP.

---

### Post by halitech on 2009-03-31
are they trying to load 192.168.1.2 from a remote location or another address?

I find using a free service like dyndns and having a static hostname for my dynamic IP easier then trying to remember the IP all the time

---

### Post by mlentink on 2009-03-31
What do you want to do? 
It's ok for your router to forward requests to certain ports, but is there something to listen?

---

### Post by Jjjakal on 2009-03-31
I haven't been linking to 192.168.1.2.  I set up that local IP as the DMZ host so it can be accessed as my real IP, and then I set that IP up with a DNS host so the server can be used as [http://thedeal.mooo.com](http://thedeal.mooo.com) 

mlentink, I see what you're getting at, and I could be wrong here, but shouldn't setting up my server as my router's DMZ host avoid any problem with listening ports?

---

### Post by dmizer on 2009-03-31
While DMZ is easier to setup than port forwarding, DMZ exposes your entire computer on all ports and gives you zero firewall. DMZ also does not garantee that port 80 will land on your server. In order to do this properly, you'll need to pull your server out of the DMZ and configure port forwarding.

---

### Post by halitech on 2009-03-31
> **Jjjakal said:**
> I haven't been linking to 192.168.1.2.  I set up that local IP as the DMZ host so it can be accessed as my real IP (72.73.x.y), and then I set that IP up with a DNS host so the server can be used as [http://thedeal.mooo.com](http://thedeal.mooo.com) 

mlentink, I see what you're getting at, and I could be wrong here, but shouldn't setting up my server as my router's DMZ host avoid any problem with listening ports?

first off, you may want to remove the IP address from your post.

second, the hostname and IP do match up and I can ping them from here in Canada so that seems to be working. Seems like there is something not going right on the server side. Does the computer you want to use as the server actually have the 192.168.1.2 for an address?

---

### Post by Jjjakal on 2009-03-31
> **halitech said:**
> The hostname and IP do match up and I can ping them from here in Canada so that seems to be working. Seems like there is something not going right on the server side. Does the computer you want to use as the server actually have the 192.168.1.2 for an address?

Good to know that the DNS host is working fine.  As for the server side connection, ifconfig does return 192.168.1.2, however I think I might have messed something up in the server settings.  Is there some way to re-run the tool that was used when installing ubuntu that auto set connection settings?  I restarted the server just a few minutes ago, and now I can't even access the server locally.  I get the same error as from a separate network.  (No idea if this is good or bad)

Edit: An interesting note, I only get a connection reset error when browsing to the server, but connecting to it through FileZilla or Putty works just fine.

---

