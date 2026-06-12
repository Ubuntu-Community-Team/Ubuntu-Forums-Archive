---
title: "Another Internet Connection Sharing Issue"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by cside on 2008-06-23
Hi All

I have been through as many posts as I can find for looking for my solution but to no avail.

What I want is to connect an Ubuntu laptop (hardy heron) through a Windoze machine to the internet, via a wireless network. The windows machine is using XP SP3.

I have an ISDN line and I am battling to get any type of connection with my current setup. Apparently ADSL should be available within the next few months, and hence my reluctance to try configure my ISDN. 

My current setup for the network is that I have ICS setup on my XP machine using IP address 192.168.0.1 Subnet 255.255.255.128, and then a WRT54GL router as 192.168.0.100, also subnet 255.255.255.128. My laptop is using roaming and the WRT54GL is set as a DHCP server as well so I usually get 192.168.0.3 or 4 subnet 255.255.255.128. I have tried tweaking my Ubuntu laptop to use a gateway 192.168.0.1, but still no joy. 

I am unsure of the configuration needed for the router as well as where I may be going wrong with network settings. 

When I start up ethsl0 uses 192.168.0.1, but I change this manually to 192.168.0.10 using ifconfig. If I dont do this, the ping time to ...0.1 is less than .04ms, whereas once I know I am pinging my XP box it goes to 2.5ms.

The crazy part is that one day when I was just playing around with the laptop, I connected without even trying to set anything up, so I know my setup must work as well as knowing that what I am trying is possible.

Any clever guys out there that can help?

---

### Post by superprash2003 on 2008-06-23
in your terminal type ifconfig and post output here

---

