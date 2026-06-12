---
title: "External to internal IP"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by MacPC on 2007-05-17
Hi,

I have serval machines in my office. Among them, one Ubuntu box internal ip 192.168.1.100 and a Mac box internal ip 192.168.1.101. The Ubuntu box is a LAMP server and the Mac box is also a web server. They share one external ip via a router. I have obtained a domain name through DynDNS.

When I am on the road, I can get on to my Mac using the DynDNS domain name. My question is, how can I get on to my Ubuntu box?

The DynDNS domain name is my comcast ip, is there a way I can specify which internal ip (Mac or Ubuntu)  I want to use as my server when I am on the road?

Thanks in advance.

MacPC

---

### Post by newlinux on 2007-05-17
You would use your router to forward the appropriate port to the appropriate machine. What service are you trying to access over from the Internet? Find out what port that service runs on, and then forward a port on your router to that port on your computer (you specify IP address and port in your router settings). Hope this helps.

---

### Post by eentonig on 2007-05-17
Normally, you should be able to instruct your router to forward external connections to a specific port, to go to an ip address internally.

If you have a decent/complex enough router, you should also be able to change that external port to something else internally. If that's possible, you could set up

public_ip on port 80 >> private_ip1 on port 80
public_ip on port 81 >> private_ip2 on port 80

you would then be able to connect to your second machine via [http://public_ip:81](http://public_ip:81)

---

