---
title: "make lamp server accept connections from internet"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by soumen08 on 2008-03-27
Hi,
Im running Gutsy Gibbon and have installed the lamp stack following a walkthrough and i think i have got it running as well (if i type localhost on firefox it shows me the page index.html in /var/www). We have a wifi network in our college and i've tried to connect to my server by typing my ip address (obtained from connection information) into my friends browser but it cant connect to the server at my ip address. I read on the web that it by default isn't accessible to external computers. How can i make it accessible?
Thanks

---

### Post by Eiríkr on 2008-03-27
That depends in part on how the university wifi network is set up.  If your server IP address looks like 192.168.xxx.xxx, and the wifi router you connect to has a similar address, and your friend's machine does too, then chances are good you're all on the same subnet, and the trouble might be a firewall somewhere.  If any of the addresses in between don't match, then you'll have to figure out what your machine's external IP address is, and then configure port forwarding on your router.  

Cheers,

Eiríkr

---

### Post by soumen08 on 2008-03-27
all our ip addresses look similar and the ip addresses are 172.16.91.xxx this isn't actually a university made network but a commercial network purchased by the university to provide internet to our block of hostels. there are no blocked sites and we should be able to configure apache to recieve external connections (external as in within the same wifi network not the internet). In the last somewhat incomplete discussion on this someone said about having to edit apaches configuration files to make it allow requests from ips other than 127.0.0.1     Can someone tell me how to do that?

Cheers,
Soumen

---

