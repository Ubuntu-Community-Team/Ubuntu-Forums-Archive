---
title: "[SOLVED] KVpnc Config Files"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2008-06-30
I am using Kubuntu 7.10. Where are KVpnc's config files located?

I am asking, because I can connect to my Windows VPN; can ping the virtual IP address pn ppp0 and the first host from the route tables, but I cannot ping beyond that point. I have a working Ubuntu 7.10 config file %gconf.xml with all the settings for NetworkManager's VPN. However, I am having trouble mapping each of these settings to KVpnc's settings.

I figured if I could look in the config file for KVpnc, I could sort out the differences.

Thank you.

Edit:
---------------------------------------------------------
Here is the solution:

Hello
 The EXACT location is: /home/<username>/.kde/share/config
 (Go to places -> home folder and press cntrl+H to view hidden files)
 name is kvpncrc
 Note:  you should never modify it (because its an app config file)
 Regards
 Bhavani Shankar.



From 
[https://answers.edge.launchpad.net/ubuntu/+question/37916](https://answers.edge.launchpad.net/ubuntu/+question/37916)

In this case, because I did not configure KVpnc to launch under my username -- requiring sudo's password -- this file is in /root/.kde/share/config/kvpncrc.

---

