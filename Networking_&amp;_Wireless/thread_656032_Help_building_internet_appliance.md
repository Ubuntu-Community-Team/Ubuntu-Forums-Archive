---
title: "Help building internet appliance"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by JoeCajola on 2008-01-02
Hi all,

I'm fairly inexperienced with linux, but ready to get my hands dirty ;p
I've installed Gutsy on my laptop (triple-boot with Vista and XP) and got a Hauppauge Nova-t USB and MythTV running, so I'm familiar with gksudo and various shell commands hehe. I also know how to operate google ;o

I'm going to build an internet appliance based on Ubuntu server, but wanted to ask a few question before I get stuck in.
I want to have 3 WAN interfaces; an ADSL connection, a wireless connection and an HSDPA connection.
To begin with I will be using some fairly old hardware (PentiumIII) and assorted NIC's.
Is there any drawback to using older hardware as a test platform?
Is Ubuntu server the best platform to use? (I looked at LEAF, but didn't want to be that restricted. I may later use a similar box to act as a mythbackend/fileserver etc)
Now the biggy, how do I prioritize which WAN connection gets used? My order of preference is wireless, ADSL, HSDPA. I have no desire to bond these connections, they are only to be used as failovers.

Sorry if I have posted this in the wrong place, it's my first post on this forum.

Cheers,

---

### Post by JoeCajola on 2008-01-02
Well, I got lucky with google.
For anyone else wanting to do the same as I, you may find the following links invaluable.
[http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/](http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/)
[http://blog.taragana.com/index.php/archive/how-to-configure-dual-adsl-cable-connections-firewall-gateway-nat-with-shorewall-firewall/](http://blog.taragana.com/index.php/archive/how-to-configure-dual-adsl-cable-connections-firewall-gateway-nat-with-shorewall-firewall/)

---

