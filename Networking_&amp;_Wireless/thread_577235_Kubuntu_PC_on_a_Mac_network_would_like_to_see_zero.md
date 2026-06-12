---
title: "Kubuntu PC on a Mac network: would like to see zeroconf / Bonjour shares"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by rkent on 2007-10-16
So, I just plugged my Kubuntu laptop into a Mac Airport Express network with a couple of other Mac nodes on it.  My roommates can all share their files via Bonjour, and I want in!  I opened my "Remote Places" -> "Network Services" panel on Kubuntu (bringing up the URL zeroconf:/), but nothing happened.  

I have poked around a bit and I found this thread: [http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

I've followed most of the advice in it, but since I don't want to serve, only browse, I skipped the FTP daemon.  i installed all the other recommended packages, though.

And still... nothing!  What else do I have to do to get bonjour / zeroconf networking going on my Kubuntu laptop?  I'm running 7.04 btw.

EDIT: so it was at least partially a firewall problem; now I've enabled all the right IPs and ports in Guarddog, and I can see that there are services out there (e.g. with Avahi-discover), but I still can't get konqueror to open any file shares or anything.  Oddly, I *can* open ssh and VNC shares - what gives?  Am I partially configured somehow?

---

