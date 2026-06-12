---
title: "[SOLVED] Broadband connection problems when using torrent clients"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by bambule on 2007-09-23
Hi!

I am using feisty and have a problem with my internet connection when running a torrent client. I' ve tried Azureus and Deluge yet, but it seems the problem is not the client itself.

I start the client and client is starting leeching / seeding. After a random time, the internet connection does not work anymore. I have to close the torrent client program and reset my router. When the DSL-Router has resync'd my connection is fine again.

My PC is connected via a switch to the DSL-Router (thomson speedtouch).

Any ideas?

-ba-

---

### Post by bambule on 2007-10-29
Hi again! 

Ups- I think this post is a little bit off-topic, because i don't think it's a problem with my ubuntu-installation. 
Anyway...
Could it be, that the modem is limiting the maximal number of connections?

I have the problem too, when more than one computer in my lan is running. The second PC has Windows XP installed and if the connection problem exist, the windows-pc doesn't get connection too.

BT client is running on linux, and for example skype on the windows-pc --> no surfing is possible any more.

I've googled for the problem, but i still can't find a solution. I'm looking for a way to increase the maximal number of connections of my sppedtouch modem. Any suggestions?

Thanks,
-ba-

---

### Post by bambule on 2008-01-21
Actually it was an DNS-Problem. I had the ip of the router in my /etc/resolv.conf, that worked so far. But sometimes the DNS-Server of the speedtouch modem has a problem and apparently this affects  the connections from the windows-computer too.
Now i've put the DNS-ip's from my isp in resolv.conf and everything is fine. :-)

Wow- that was a kind of monologue...

---

