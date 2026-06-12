---
title: "Bonded connection and use"
date: 2016-10-24
forum: Networking &amp; Wireless
---

### Post by knowonecanknow on 2016-10-24
In the past I configured a bonded connection on my Ubuntu 16.04 server and I always thought it was working.  Recently I ran bmon while a file transfer was in progress and then I saw all the traffic being sent to an IP address of another port not part of the bond, despite using the specific IP of the bonded connection.  I am not convinced I ever finished setting up the bond correctly but it led me to believe it was up.  

For some background.  I have a HP 4 port card that I installed into the machine ([https://www.amazon.com/gp/product/B000P0NX3G/ref=oh_aui_detailpage_o06_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B000P0NX3G/ref=oh_aui_detailpage_o06_s00?ie=UTF8&psc=1)) and these are the ports I bonded together.  The bonding was done in the /etc/network/interface file ([http://i.imgur.com/x836cVc.png](http://i.imgur.com/x836cVc.png)).  This file is all sorts of weird to me now.  Why I commented out the manual configuration while using manual I don't recall and deleting the comments causes the network service to not start.  Either way the Bond0 was meant to be IP .110 while eth0 was to be .101 (here is the ifconfig [http://i.imgur.com/S937h9R.png](http://i.imgur.com/S937h9R.png)).  I also, have these 4 ports plugged in and configured as LAG with my Cisco SG200-26 26-Port Gigabit Smart Switch.  Here is how the config looks if it helps ([http://i.imgur.com/FnMTjHQ.png](http://i.imgur.com/FnMTjHQ.png) and [http://i.imgur.com/ES1RUZ9.png](http://i.imgur.com/ES1RUZ9.png)).  My Verizon mandated router is the DHCP host for the network.  I have it to DHCP from range of .002 - .099 reserving .100 for the switch and I wanted .101 for eth0 and .110 for bond0. Eth0 is plugged into the router directly and has all the port forwarding done to that port, ssh etc.  Meanwhile, IP .110 was meant to be for internal file transfers.

Now to the issue I noticed.  I connected to my samba shares just by typing in 192.168.1.110 into my windows machine and drag and drop files to and from.  Since I connected to the machine via typing in the specific address I always assumed I was sending files over that port.  I installed and ran bmon the other day and realized that despite connecting to samba with .110 all my files were being transferred .101 instead ([http://i.imgur.com/p8wu4Kj.png](http://i.imgur.com/p8wu4Kj.png) and [http://i.imgur.com/hWS0fjZ.png](http://i.imgur.com/hWS0fjZ.png)).  I even unplugged the cord from eth0 and when I did that the bond0 broke as well.

Can I have some help on to properly configuring my bond0 to be the static IP address of .110 and eth0 to remain as .101 so I can ssh through that port.  I don't really care if the 4 port card is static IP or not as long as the bond itself is.

Thanks!

---

### Post by shersk on 2016-11-08
Where is the official documentation for connection bonding? Anybody? It's integrated in network-manager, so it should be documented somewhere.

---

