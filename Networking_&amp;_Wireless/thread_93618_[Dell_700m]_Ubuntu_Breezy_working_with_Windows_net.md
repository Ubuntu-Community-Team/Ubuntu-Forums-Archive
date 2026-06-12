---
title: "[Dell 700m] Ubuntu Breezy working with Windows network ???"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by jmejedi on 2005-11-22
I have a Windows (home) newwork [ethernet] , and I want to connect my Dell 700m laptop into this network in order to go on the internet, share files, etc.... I know / understand the following: Every pc in my network (Windows) must have a IP address so that each can see each other on the network; using 4-port hub and all Windows pc have McAffee protection (that is, firewall, anti-virus, etc..). Currently, I am able to connect to the internet and that's great, but........ I notice that when I try to come over to this forum using my dell 700m running ubuntu breezy, sometimes it is unable to connect to this website and somtimes it can, also, when I try to "sudo apt-get update" from home (in my network), I get some errors/warning saying couldn'g connect to some of the responsties.... opps, can't spell...... I have given my ubuntu running pc an IP address...... everything is fine, except I notice the above problems / discrencies........ I guess my real question is the followIng: "Is there a good tutorial over how to get a ubuntu pc working perfectly in a Windows network ???"............................ also, I have my other pc know/allow my dell 700m running ubuntu breezy know about it in their firewall properties..........

Thank you for your time,

JME

---

### Post by mips on 2005-11-22
Some more info please.

Do you have a router (Brand & Model) ?

It sounds like you have DNS problems. Try disabling IPv6.

[http://ubuntuforums.org/showthread.php?t=78337&highlight=Option+IPv6](http://ubuntuforums.org/showthread.php?t=78337&highlight=Option+IPv6)

---

### Post by jmejedi on 2005-11-22
I have a Linksys "Ethernet Fast Cable / Router" model BEFSR41; which I am using as a hub; it is actually being used as a hub (in my case). Also, I am having all my computers connect to the internet through my main PC; it is sharing internet connection with the rest of my network.

Thanks for your time,

JME

---

### Post by mips on 2005-11-23
Are you using a static IP or DHCP on the Ubuntu machine. What are your DNS settings for this machine ?
What are the network seetings for the windows machine.

---

### Post by ruffneck on 2005-11-28
I also have mostly the same equipment as mentioned above (i.e. a 700m laptop and windows network setup)

I have a ubuntu box with two nic cards. eth0 connects to cable modem and eth1 connects to a hub, which goes to the local net providing NAT. I use Firestarter to do my internet connection sharing on the ubuntu box, allowing all private addresses to have full access to the interent etc. 

I use Samba to create network shares on the the 700m (running ubuntu also) and ubuntu box. 

This setup works a charm. I am able to surf and see all my puters on the network. 

About your repositories, you may need to update them for breezy (assuming you're running that)

Check here:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

