---
title: "OpenVPN on 14.04.2 access from Smartphone OK but not Win7"
date: 2015-07-25
forum: Networking &amp; Wireless
---

### Post by Ponders on 2015-07-25
I am sure this have been asked many times but none as specific to address this particular issue.

I have setup OpenVPN on Ubuntu Server 14.04.2 and after some troubleshooting, I am able to log in and access internet on my OpenVPN server from my smartphone (Android using OpenVPN app), I have checked the IP from my smartphone and confirmed it to be the public IP of my OpenVPN.

However, I can't say the same for my Laptop running Win 7 Professional 64-bit. I am able to log in using OpenVPN GUI (run as admin) but that's about it, I am unable to SSH the server not use the internet. 

The server is located in my workplace remotely accessed using the same internet (from both smartphone and Laptop) from home.

Because internet worked fine on the smartphone, I believe the config on the Server side is ok. Is there any additional configuration that I have to add specific for Windows environment?  Or are there additional tasks that i should carry out on the Win 7 end?

> push "route 192.168.0.0 255.255.255.0"push "redirect-gateway local def1"
push "dhcp-option DNS 8.8.4.4"

has already been added in the server conf file.

I am suspecting the problem lies at the TAP adaptor on the Win7.

---

