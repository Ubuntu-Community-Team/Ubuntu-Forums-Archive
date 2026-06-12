---
title: "Can someone explain to me the Ubuntu VPN Wiki?"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by Isoss on 2008-10-06
Hi,
I've been having hard time connecting to VPN, and now trying to configure it manually and run it from command line. Here is a vpn wiki [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN) where it explains how I can do it from the command line. The problem is that I can't get some terms!
In file /etc/ppp/peers/YOUR_COMPANY
What is YOUR_VPN_GATEWAY? Isn't it the IP address provided by the ISP?

What does it mean: YOUR_COMPANY in "ipparam YOUR_COMPANY" ?
And the line after it remotename YOUR_COMPANY, is it the same?

ALso
name YOUR_DOMAIN_OR_SERVER_NAME\\YOUR_VPN_LOGIN
What does YOUR_DOMAIN_OR_SERVER_NAME\\YOUR_VPN_LOGIN mean? or what is \\ in the first place?

It's really not so clear putting strange variables without explaining. I know that they are written in english indicating the value, but they must be more explained. 

Please, help me understand that I may put the right values, cuz it's confusing, and although I tried a lot I couldn't get it to work.

Thanks.


Now in file /etc/ppp/chap-secrets,
I must type: YOUR_DOMAIN_OR_SERVER_NAME\\YOUR_VPN_LOGIN * YOUR_VPN_PASSWORD *
What bout password? Is it between ** ?

---

