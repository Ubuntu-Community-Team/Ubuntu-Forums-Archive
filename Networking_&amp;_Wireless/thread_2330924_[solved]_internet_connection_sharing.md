---
title: "[solved] internet connection sharing"
date: 2016-07-16
forum: Networking &amp; Wireless
---

### Post by DrScum on 2016-07-16
I have a new ubuntu 16.04 desktop installed which through a wireless card is connected to the internet and runs a dhcp server for a wired subnet. I want to share that internet connection to all systems connected to the subnet.

I followed this [http://askubuntu.com/questions/359856/share-wireless-internet-connection-through-ethernet](http://askubuntu.com/questions/359856/share-wireless-internet-connection-through-ethernet) but wasn't successful.

How do I do this correctly?

Thanks for your consideration.

---

### Post by DrScum on 2016-08-03
Meanwhile I have proceeded to a point where I can ping the google dns server (ip 8.8.8.8) from a system connected via LAN to the dhcp server. But when I try to use a browser to reach google I get "server not found". Any help?

---

### Post by DrScum on 2016-08-10
more specific information:
the DHCP server has a wireless card IPv4 set to "Automatic" and receives its IP from the wireless router connected to the DSL-modem
the DHCP server has a wired card IPv4 set to "Shared to other computers" 
the client has a wired card IPv4 set to "Automatic" and receives its IP from the DHCP server there is no proxy set and DNS and Routes is set to "Automatic"
The client can ping the DHCP server on its IP but it can NOT ping 8.8.8.8 (despite from what I said in the post above).

So I think the problem seems to be the routing through the DHCP server. The the client request to ping the 8.8.8.8 adress doesn't seem to be going from the subnet to the internet.
Where do I have to make changes to make this work?

---

### Post by DrScum on 2016-08-12
I couldn't make this work the way I wanted but found an ok solution based on static IP adresses. Here is the procedure in case someone else has a similar problem and ends up in this post: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) I followed the "Ubuntu Internet Gateway Method (iptables)".

The post also describes a procedure ("Advanced Gateway Configuration") including a DHCP/DNS server just the way I wanted it but following that procedure didn't work for me.

With this I guess my problem can be considered as kind of solved (all by myself!)

---

### Post by mörgæs on 2016-08-12
If you consider it solved please mark the thread so using Thread Tools.

---

