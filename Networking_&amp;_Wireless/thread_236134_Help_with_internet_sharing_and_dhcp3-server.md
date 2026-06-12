---
title: "Help with internet sharing and dhcp3-server"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by La1nE on 2006-08-14
Hi everyone!

It seems like i've put myself in deep sh*t again. 

This is what Im trying to accomplish:

I want this computer (Ubuntu Dapper) act as a dhcp-server, so it'll give my winxp laptop both an IP and share my internet to the laptop. I've previously succeded with internet sharing with firestarter, but that was under static ip:s. 

Ive apt-getted both firestarter and the dhcp3-server packages. Ive followed the guide at ubuntuguide.org for setting up a dhcp3-server. It works, and my ubuntu-box gives the laptop an ip, but the internet-sharing does'nt seem to work. And every time I start the dhcp3-server my internet connection dies. If i check "Networking" at the System -> Administration-button i can see that somehow my Default gateway device has changed from Eth1 to Eth0! 

This is my current eth-setup. 

Eth1 goes to my internet connection (DHCP) 
Eth0 goes to my winxp-laptop (wich i want to act as a dhcp3-server)

Also, ive noticed that when i install the dhcp3-client, it automatically removes dhcp, could that be why im having so much trouble?

I know it might seem fuzzy, but ill be glad to help with any details that might be of assistance. Any ideas/explanations/questions is more than welcome. Thx!

---

