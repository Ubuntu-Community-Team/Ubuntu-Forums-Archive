---
title: "Azureus in Ubuntu"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by rushbrad on 2007-07-12
Hey Guys, 

I just installed Azureus on Ubuntu and it runs fine for about 5 minutes until it will suddenly drop all my torrents to 0 kbps.  I have Yahoo DSL, so I imagina that COULD be a factor if it is some sort of cap, but I had Yahoo at my other apartment on my Windows PC and it never did this.  Any suggestions?

---

### Post by MacHaddock on 2007-07-12
I'm a noob at ubuntu and looking for help to another azureus problem. BUT You could try to change to ports you use. I know that some ISP's cap some ports commonly used for p2p and stuff.

---

### Post by rushbrad on 2007-07-12
Yeah I tried switchin them around but it kept happening.  When I run the NAT/Firewall test my ports always come out OK too.  Any other ideas?

---

### Post by fno on 2007-07-12
What's your bandwidth on that DSL link? Do you have a firewall or router? Many consumer market devices can't handle a lot of throughput and/or a lot of connections. The BitTorrent technology generally allows for and use many connections to many different peers.

What do you do to get it working again? Restart Azureus, restart your computer, restart your DSL modem or just waiting?

---

### Post by rushbrad on 2007-07-12
The modem gets about 1.5Mbps down for bandwidth.  It is hooked directly into the modem (no router) and to get it working again, I close it and wait a few minutes then restart it.

---

### Post by fno on 2007-07-12
Have you tried any other computer or OS? Sounds like a modem/provider not being able to handle/allowing lots of connections...

---

### Post by rushbrad on 2007-07-12
Yeah, oddly enough I can download multiple files at a time when I plug my wife's laptop with XP into the same modem.  So I am not sure what to think.

---

### Post by fno on 2007-07-12
Didi you download via bittorrent technology from the laptop as well?

---

### Post by rushbrad on 2007-07-12
Yes but with utorrent.  Although I am confident that it would work just as well with Azureus.

---

### Post by fno on 2007-07-12
Yeah, sounds likely. By the way, what network card do you have? Might be a driver related issue. Run the following commands and paste the results here:
[LIST=1]
[*]lspci
[*]sudo ethtool -i eth0
[*]ifconfig eth0
[/LIST]

---

### Post by rushbrad on 2007-07-13
Cool, I am at work right now so when I get home I will run that and see what I get and post it here.  By the way, my internet works with my Ubuntu PC when i connect directly to the modem but when I connect through my router, it connects to the network but not the internet.  Any suggestions on what to check for this?

---

### Post by fabricio.lemos on 2007-07-13
I have this same problem with Azureus. The problem was solved when I installed the Java jre 5.0.

---

### Post by rushbrad on 2007-07-13
Awesome, I will give that a try when i get home!  Thanks man.

---

### Post by don_xvi on 2007-07-19
I had the exact same problem.  Torrents would run OK at first, then stop, sometimes they'd restart for a while, but seemed to be disturbed when something happened, like clicking to force start another torrent, or when one would decide on it's own to start again.  I got pretty far off track in installing Java 5, so that Azureus wouldn't even start.  Eventually I wound up uninstalling everything Sun Java and Azureus, and reinstalled Azureus via Automatix2 and it works great now.

---

