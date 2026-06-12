---
title: "Trying to reach public web page on internal server from internal ip"
date: 2017-08-20
forum: Networking &amp; Wireless
---

### Post by Robert_Boutin on 2017-08-20
Hi,

I don't know if this is an Apache2 config issue, a NAT loopback issue, or a combination of the two.

I have a server in my basement running Ubuntu 16.04.  On this server I am running VirtualBox and inside of that I have a virtual webserver also running Ubuntu 16.04.  The webserver home page domain.com can be successfully reached from outside the network by a public static ip address X.X.X.10 which is NAT'ed through a Ubiquiti EdgeRouter X to its private ip address 192.168.1.110.

I experience the following:
From external network to domain.com
Successfully loads home page
From inside network on laptop 192.168.1.119 to domain.com
endless wait, timeout
From inside network on laptop 192.168.1.119 to virtual server 192.168.1.110
Reach the login page of the router


From inside network on physical server 192.168.1.109 to domain.com
endless wait, timeout


From inside network on physical server 192.168.1.109 to virtual server 192.168.1.110
Apache2 Ubuntu Default Page











Does anyone have a suggestion on which direction to head first?

Thanks as always

---

### Post by Andreyshel on 2017-08-20
How do you resolve your domain name?
What will happen if you run
 nslookup domain.com from laptop?

---

### Post by Robert_Boutin on 2017-08-20
I'm not sure what "How do you resolve your domain name?" means (sorry).  Can you explain?

Output of nslookup domain.com is:

Server:       127.0.1.1
Address:     127.0.1.1#53

Non-authoritative answer:
Name:        domain.com
Address:     X.X.127.10

---

### Post by Andreyshel on 2017-08-20
> [COLOR=#000000]I'm not sure what "How do you resolve your domain name?" means (sorry). Can you explain?[/COLOR]

/Complicated stuff
Computers connect to each other using ip address.
When you go to web site with your browser, domain name(e.g [www.google.com]("http://www.google.com")) needs to be replaced with ip address(e.g 216.58.209.110). This is called resolving. Usually this process goes in the background. Nslookup shows the result to you.
It works almost like your phone  contact list(phone is like ip address and name is like domain).

Resolving is performed by dns server(example is [dnsmasq]("https://en.wikipedia.org/wiki/Dnsmasq") or [BIND]("https://en.wikipedia.org/wiki/BIND")). or using  your local /etc/hosts file.
/Complicated stuff

> [COLOR=#000000]Server: 127.0.1.1[/COLOR]
[COLOR=#000000]Address: 127.0.1.1#53[/COLOR]

[COLOR=#000000]Non-authoritative answer:[/COLOR]
[COLOR=#000000]Name: domain.com[/COLOR]
[COLOR=#000000]Address: X.X.127.10[/COLOR]

Your local domain is now associated with your external ip. That is not very optimal.
Can you show your /etc/hosts file please

---

### Post by Robert_Boutin on 2017-08-20
Ah, ok, I understand domain name resolution, I just didn't understand what you meant by how do *I *resolve it.  I thought maybe there was something deeper I wasn't getting.

/etc/hosts file:

127.0.0.1       localhost
127.0.1.1       web.domain.com    web
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by Andreyshel on 2017-08-20
[COLOR=#000000]> 127.0.1.1 web.domain.com web

Is it hosts from your laptop?
[/COLOR]

---

### Post by Robert_Boutin on 2017-08-20
No, I ssh'd into the web server from my laptop to get to /etc/hosts

---

### Post by Andreyshel on 2017-08-21
In case we want your domain name to be resolved into your  webserver internal ip, hosts file on your laptop(and other local clients) should contain information about webserver.
so it should include
```
<webserver local ip> domain.com
```
line

Add it and try to visit your website (by domain) again.

---

### Post by Robert_Boutin on 2017-08-21
My problem is solved, it was a NAT loopback configuration issue with the router.  It is working properly now.

Thanks, sorry for the inconvenience.

---

