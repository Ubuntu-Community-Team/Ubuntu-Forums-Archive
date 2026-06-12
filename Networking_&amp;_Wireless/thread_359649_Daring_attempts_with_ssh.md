---
title: "Daring attempts with ssh"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Lutherian on 2007-02-12
**The mission:**
To access my Linux box remotely with OpenSSH as the server

**The Challenge**
To do it without PortForwarding

*Why?*
Because I have 2 routers 
1 x desktop SMC router (with no apparent information on how to access the configuration menu i.e. ip adress for router)

1 x router of unknown make - which is part of my Aerial / installation ( I have a wireless / radio internet link)

So even if I could port forward the one router, I would not be able to PortForward the other.

**The Clue**
What intrigues me, is this - how is it that I am able to share files with other users through my IM protocols (Gaim - Yahoo, Gaim - MSN) These users are, in a sense, connecting remotely to my computer, so why can't I - is there some way to exploit this technology to allow me to access my system remotely - even across the NATed firewalls?

So this is one for the "heavies" The smart guys - if you can work this one out, I'll have to build a statue of you and bow before it each morning as my named Guru and Mentor.

---

### Post by apollo13 on 2007-02-12
Yahoo uses a proxy server for filetransfers, same for ICQ (at least, when using gaim)

apollo13

---

### Post by jpkotta on 2007-02-14
This might help: [http://ubuntuforums.org/showthread.php?t=299608](http://ubuntuforums.org/showthread.php?t=299608)

If you need to know the ip address of your router, use nmap (or really just ifconfig).

I don't know if it's possible to have a machine outside the network bypass NAT and connect to a machine inside (without the inside machine initiating the handshake).  If it were possible, it kind of defeats the purpose of NAT.  Which is why there is port forwarding so that it's possible in controlled cases.

You might like to try a VPN like Hamachi.

---

### Post by gradedcheese on 2007-02-14
Do you really have two routers, or is the WiFi one in "access point" mode (ie: router features turned off).  I don't quiet see how having two routers (with typical routing stuff on) on the same LAN would make any sense.

What I do is DSL->Router->(LAN and WiFi AP)

Then various PCs are connected to the LAN (via a switch connected to the router) or wirelessly to the AP.  The AP just does connectivity, it does not assign DHCP addresses or anything like that (the router does it).  

You could also place a PC on the network to which all SSH (port 22) traffic gets forwarded via NAT on the first router.  SSH into that box and then, from there, SSH into whatever PC you're interested in.  The first SSH connection gets you in to the LAN from outside, the second one gets you to the desired PC.

---

### Post by Lutherian on 2007-02-20
Apologies for the delayed response.

1) gradedcheese - yes, you've hit the nail on the head, I'm sure you're quite right. I am looking in the general directions you've suggested - this is the path to setting up my system "the right way" - Thank you

2) jpkotta - you Sir, however, have given me a solution on a silver platter by suggesting Hamachi - A quick and easy way to get what I need until I devise a means suggested by gradedcheese. 

I have only one more question for jpkotta - as I must now build a statue in you honour in my backyard - please what form it should should take... a giant soaring eagle would be nice.

:P

Seriously thank you much appreciated.

---

