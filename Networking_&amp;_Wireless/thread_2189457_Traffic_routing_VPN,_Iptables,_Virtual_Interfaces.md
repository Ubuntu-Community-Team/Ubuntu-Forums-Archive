---
title: "Traffic routing VPN, Iptables, Virtual Interfaces"
date: 2013-11-22
forum: Networking &amp; Wireless
---

### Post by bumperjeep on 2013-11-22
Hello everyone,

I'm new to the boards here, but I've been using Ubuntu for a number of years now. I have a complicated question that I need some advanced networking help with. 
Here is my goal: Seperate network traffic. I want use my paid vpn service provider to encrypt the connection for a single application.  The rest of my network applications I want to operate outside of my vpn.  It doesn't matter to me how I manage this goal: I have two network cards available - the default one in my motherboard and I have a spare pci NIC. I will install that extra nic if I need to but I'd prefer to somehow use virtual interfaces. I want to be able to use port forwarding for the rest of my network applications so they can hit the internet so i access them remotely I'm using Ubuntu 12.04. 



I've used this website for reference. I'm thinking I need to try and bind the vpn to a specific interface with the bind or local command. 
[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux)

I know there are some really smart people here, I hope somebody can help!

---

### Post by mellocode on 2013-11-22
Can you configure that single application to use a proxy and point it at your VPN? I'm not entirely sure how you have configured your setup but there are a few options. What VPN are you using? Is it OpenVPN or another?

---

