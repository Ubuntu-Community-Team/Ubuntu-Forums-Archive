---
title: "Analyze Network-Wide traffic"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by jflash on 2007-01-27
I have a home network with three computers (1 XP Media Center Edition, 1 XP Home, and 1 Ubuntu 6.10). Currently, the network is set up like this:

Cable from wall --> cable modem --> Linksys WRT54G router --> {computers}

Now, my point in saying all this is that I would like to be able to monitor network traffic for every computer using Wireshark/Etherape or a similair program. (I particularly like Wireshark, but if there's something better out there, I'm open to suggestions.) My problem is figuring out the best way to connect everything (as in hardware, not software) without making everything dependent on my computer (the one I'm wanting to use for the monitoring, which has Edgy installed) or rewiring the whole network. I do have two ethernet ports on my computer if it makes any difference. If anyone has any suggestions, they would be much appreciated. Thanks!

---

### Post by kingmonkey on 2007-01-27
[http://www.howtoforge.com/zabbix_network_monitoring](http://www.howtoforge.com/zabbix_network_monitoring)

[http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-analyze-network-traffic-with.html](http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-analyze-network-traffic-with.html)

I guess it all depends on how much sniffing you want?

---

### Post by tturrisi on 2007-01-27
The only traffic you can monitor with your current setup is your own.  This is because all lan computers are connected to a switch (the router has a built in switch).  To monitor all traffic you would have to do:
modem > router > hub > 3 computers.
A hub is different than a switch because any traffic going into a hub gets sent to all computers connected to it, whereas a switch is a bit smarter & routed traffic to only intended destinations.

My home lan is similar and when my kids were younger I had the 3 of them connected to a hub & hub connected to the router.  When I wanted to see what they were up to I just plugged my box into the hub & ran ethereal.

---

### Post by RandomJoe on 2007-01-27
There are a couple of options for doing what you want - if you are open to flashing your WRT54G (and it's a model that you can do that to) there are some firmwares for it that will track the traffic and report back to your computer running the client-side part of the tracker.  (I read about it, thought "that's interesting" and that's it, so I don't remember what program they are using...)

Otherwise, the only way is - as you said - make everything dependent on your system being up.  Alternatively, if you can come up with an older "spare" machine for free/cheap, you can replace the WRT54G with a bonafide Linux firewall box - and run your tracking software there.  

Using your computer or a spare, run the cablemodem in one NIC, another NIC out to your LAN.  You can still use the WRT54G as a switch/AP if you want - just plug the firewall into one of the regular switch ports (the WAN port is unused).  I do this at home, works fine.  You have to enable port forwarding (if it isnt' already) and BE SURE your firewall is set up correctly, as the computer replacing the 54G is now directly on the 'net with no other protection.  (I'm not a lot of help here with Ubuntu - my firewall runs a cut-down Slackware and I hand-crafted all my firewall and network config scripts!)

---

