---
title: "Switched ISPs, internet no longer works"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by randomalphanumeric84 on 2007-02-19
Hello everyone,

I have recently come upon an unexpected problem setting up my new Ubuntu system and have been unable to solve it.  Specifically, I cannot access the internet.  Some details:

I initially installed Ubuntu 6.06 on two computers at a friend's house.  After installation, I plugged into his router (I believe a linksys WRT54G, the ubuquitous blue box that everyone has) and without changing or setting anything up immediately had internet access, which I used to download patches, etc.  I then took the boxes home and plugged them into my router, also a WRT54G, but was unable to get internet access.  It appears windows boxes plugged into the router can access the internet, but mine cannot.  

I initially went to system->administration->networking and changed the eth0 settings to static IP, 192.168.1.10, 255.255.255.0, and 192.168.1.1, but could still not get internet access, even after rebooting.  With this setup, the two boxes can see eachother, that is, I can rsync files between them on the LAN, and I can also open up a connection to my LAN router through ubuntu, I just get nothing when I open up firefox and put in [www.yahoo.com](www.yahoo.com).  Likewise I get nothing when I directly put in the ip address of yahoo xxx.xxx.xxx.xxx.   I tried switching it back to DHCP (which is enabled on the router) and could not get internet access.  

Based on some reading in these forums, I checked out my /etc/resolv.conf file and it appears to still be configured for the internet at my friend's house, that is, its something to the effect of

search comcast.net (my current ISP is covad, my friend had comcast)
nameserver xxx.xxx.xxx.xxx (not on my local domain, and not the nameserver given to me by my ISP, likewise not the nameserver supported by my router.)
etc...

My next step was going to be to manually change this file by deleting the line 'search comcast.net' and adding 192.168.1.1 (my router's address) as the first nameserver when I get home this evening; I was then going to restart the networking using /etc/init.d/networking restart.  I wanted to see if anyone had any other ideas, or if there were any other configuration files I should be checking out.  Should I change the nameserver to my router's address or the DNS server addresses my ISP gave me?  Also, should I be changing this file at all as it appears it was automatically set up when I first connected to the internet?   Any thoughts would be appreciated.  I'm still quite impressed with Ubuntu despite all this.

---

### Post by MrFSL on 2007-02-19
As always start with the basics:
1) Can you ping your router? 
**ping 192.168.1.1**
2) If you cannot then don't worry yet about your nameserver issue; first fix your networking issue with the router. If you can then lets ping through your router:
**ping [www.google.com](www.google.com)**
3) If google is unreachable then lets try pinging by ip address. Here at my home [www.google.com](www.google.com) resolves to 66.102.7.147
4) If you can't ping the ip address then you probably have a networking issue between your router and your isp (cable box, DSL modem, etc)
5) To reslove issues with your router and your isp read the manual for your router and contact your isp.
6) If you CAN ping an outside IP address then you have a nameserver issue. On these home Linksys routers you can setup the routers address as your nameserver by editing /etc/resolv.conf and replacing all the text with:
**nameserver 192.168.1.1**
and restarting networking or restarting the computer.

Hope this helps.

---

