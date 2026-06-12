---
title: "RDP over VPN Doesn't Work"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by ChevyGuy on 2006-10-21
Hello, just started with Linux, so please forgive me if I use a lot of Windows terms.  I'm trying to connect to the Windows domain at work.  I can do it fine using PPTP and Remote Desktop from XP Pro.  I can connect to another XP box on my home network using the Terminal Server Client in Dapper.  I can connect to work using pptpconfig and ping clients.  If I try to connect to a workstation or terminal server via IP address using the Terminal Server Client in Dapper I get 'Connection Refused'.  I've tried an unused IP & get a message that the client wasn't found so I'm guessing that the Terminal Server Client is finding the machine on the network at work.  I've tried to telnet into a server at work over the VPN & get nothing, it just hangs.  I've tried scanning ports using Network Tools and get nothing.  Any ideas?

---

### Post by ChevyGuy on 2006-10-22
Okay, got it working.  I'll bet you Linux people never thought I had it in me!  Anyway, I just had to set up routing in pptpconfig. Again, I'm used to windows where more things are automatic for us dummies!  Here's what I don't understand.  The other end of the VPN tunnel ended in a private network, 10.3.48.0.  Yet, when I pinged I got an answer.  Running traceroute I was able to figure out the VPN traffic wasn't going out the VPN but out the default gateway to the internet.  IP address ranges shouldn't go thru internet routers, yet the last hop was to 10.3.48.7.  RDPv5 works well now.

---

