---
title: "how to connect to computers with invalid ip from outside network"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by D!V00NE on 2008-05-18
hi

i wanna know if there is a way to connect to computers inside a network that have invalid IPs from outside of that network.

for example connecting from home to work computer. knowing that work computer has an invalid IP and connected to the server with valid IP. we know server's username and password. server has two network adapter. one with invalid ip and other with valid ip.
if it helps server has ubuntu 7.10 desktop edition. work pc has ubuntu 7.10 too :?:

thanks.

---

### Post by Mobiplayer on 2008-05-18
What do you mean with "invalid IP"? Maybe you are referring to a "Private IP" like in 192.168.X.X, 10.X.X.X, ...?

---

### Post by Monicker on 2008-05-18
> **D!V00NE said:**
> hi

i wanna know if there is a way to connect to computers inside a network that have invalid IPs from outside of that network.

for example connecting from home to work computer. knowing that work computer has an invalid IP and connected to the server with valid IP. we know server's username and password. server has two network adapter. one with invalid ip and other with valid ip.
if it helps server has ubuntu 7.10 desktop edition. work pc has ubuntu 7.10 too :?:

thanks.

If you are referring to RC1918 ip addresses (which are indeed valid), then NAT must be used to communicate between private ip addresses and public ip addresses.  This usually occurs at the gateway device - router, firewall, etc.

[http://www.faqs.org/rfcs/rfc1918.html]("http://www.faqs.org/rfcs/rfc1918.html")

---

### Post by chickpea on 2008-05-18
I guess you use the term "invalid IP" for "Private IP" and you want to log in a computer in your office network through the Internet when you're at home.  If my suggestion is right, you need to use any tunneling protocol like PPTP or IPsec.

---

### Post by D!V00NE on 2008-05-19
> I guess you use the term "invalid IP" for "Private IP" and you want to log in a computer in your office network through the Internet when you're at home. If my suggestion is right, you need to use any tunneling protocol like PPTP or IPsec.
yes. i mean private ip like you and "Mobiplayer" said 192.168.xxx.xxx . and like "Monicker" said i have a router. anyway is there a way for that.

thanks.

---

### Post by chickpea on 2008-05-19
Sorry but I can't tell any application for Linux that offers services you need. I'm new to Ubuntu and Linux as you see from my "Join Date". 
But I can at least say the networking service you need is so called "VPN"(Virtual Private Network) and there exist various kinds of VPN protocol. 
If you post more information about how your home and office network are designed, some Linux network experts will tell you which VPN protocol to choise and how to run VPN on Linux, I guess.
So why don't you post an image of your network as shown below? Make sure to give vendors and products names of your routers. It's very important about this issue:)

[IMG]http://www.letme.be/common/network.gif[/IMG]

---

### Post by D!V00NE on 2008-05-20
> **chickpea said:**
> Sorry but I can't tell any application for Linux that offers services you need. I'm new to Ubuntu and Linux as you see from my "Join Date". 
But I can at least say the networking service you need is so called "VPN"(Virtual Private Network) and there exist various kinds of VPN protocol. 
If you post more information about how your home and office network are designed, some Linux network experts will tell you which VPN protocol to choise and how to run VPN on Linux, I guess.
So why don't you post an image of your network as shown below? Make sure to give vendors and products names of your routers. It's very important about this issue:)

[IMG]http://www.letme.be/common/network.gif[/IMG]

i'll post it as soon as i'll get it.
thanks.

---

