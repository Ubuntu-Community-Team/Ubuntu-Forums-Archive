---
title: "Wireless Bridge from Ubuntu MATE 18.04.2 to Windows 10"
date: 2019-11-28
forum: Networking &amp; Wireless
---

### Post by ssj7yl3r on 2019-11-28
Hello everyone. 

I am trying to establish a wireless bridge from my Raspberry Pi 3b+ running Ubuntu 18.04.2 to my Windows 10 Desktop. 

So far I have done these steps:

- Within Ubuntu, open Network Connections > Add new connection > Select "Bridge" in drop-down menu > Under Bridged Connections, select Add > Select "Ethernet" from the drop-down menu > Select my ethernet device in Device drop-down menu (eth0 (MAC address) ) > Save > Save again. 

I've verified under Network Connections that the new "bridge0 slave 1" is the only Ethernet connection showing up, and my new "Bridge connection 1" is showing under Bridge, and I am connected to my WiFi with internet access. I've also confirmed that under both the bridge and the slave I have checked "Automatically connect when available" and "All users may connect to this network." Also, I've not changed any IP configurations away from Automatic DHCP, so IPs should automatically be assigned. 

I plug in Ethernet to both sides and Ubuntu tells me I am connected via the Ethernet connection. 

Over on my Windows 10 PC, I am shown that I am connected to an Unidentified Network, and there is no internet connection. I am not exactly sure what I have to do from this point to get Windows to identify and use the bridge properly. 

I've tried running the Windows network diagnostic tool, and it gives me this message: 

"Ethernet" doesn't have a valid IP configuration - Not fixed.

Maybe it is possible to use manual configurations to match up IP addresses, etc.? Not quite knowledgeable myself to know unfortunately. I appreciate any help in advance.

---

### Post by ssj7yl3r on 2019-11-29
Hey everyone.

I ended up finding a solution to this problem myself. 

I followed [this guide](https://askubuntu.com/questions/359856/share-wireless-internet-connection-through-ethernet/368231#368231) to get it working. You only need to use steps 1-4, and my Windows 10 machine automatically found the network and began working as it should. I wasn't expecting much, but the 3 B+ can transmit 75Mbps download and upload (I have a Gigabit to my home). Pretty cool! 

Basically just skip using the bridge method and alter a regular Ethernet connection as instructed in the guide. I would imagine this method should work for any ethernet device needing internet. 

Hope this helps someone else!

---

