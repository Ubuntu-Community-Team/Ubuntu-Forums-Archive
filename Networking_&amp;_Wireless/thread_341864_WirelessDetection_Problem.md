---
title: "WirelessDetection Problem"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by jimbren on 2007-01-19
I've put together a frankenputer and I'm having an odd problem that I haven't experienced before.  I'm using a Netgear MA311 wireless PCI card that has been used in other systems and multiple Ubuntu installations on other computers.  

When doing an installation of Kubuntu 6.10 on this system, the card is detected properly, I'm asked for my WEP key (I'm not using WEP, so I leave this blank), it configures the card using DHCP, and proceeds without an issue.  

Once installation is complete, I don't have any wireless and I can't see the card in System Settings\Network Settings.  

When I look at /etc/networking/interfaces, it does show that I'm using eth0, with my ESSID set to any.

When I do a lspci, it shows the wireless card, and when I do an lsmod, it shows that the orinoco driver is loaded and associated with the card.  But still, it's not there and I can't load it.

What am I doing wrong?

Thanks,

jimbo.

---

### Post by teaker1s on 2007-01-20
install
wifi radar or similar  to see if card is working, as your using kde I'm not really sure what to suggest

---

### Post by jimbren on 2007-01-22
I was able to get around the problem in a very round about way.  I did installs with a 6.10 server CD and a Kubuntu 6.10 alternate install CD, all with the same result.  The system only has 128MB of RAM, and I couldn't get 6.10 live CD to actually kick off the install process.  

I also have a Kubuntu 6.06 live CD, and I was able to get it to load.  After confirming that it properly detected the wifi card, I sucessfully installed using that CD, and it uses the card with no problem.  

I'm not sure why the 6.10 CDs didn't do the job, especially since they properly detected and configured the card during installation, but it is up and running, so I'm just writing it off as a hazard of parting out old computers and moving on.

It's a clunker--P3500 with 128MB of RAM--but I'm only using it remotely so I disabled KDM from startup and it is doing it's job as a backup server without any problems.  

Thanks for the suggestion.  I'll file it away in case I run into a similar problem down the road.

jimbo.

---

