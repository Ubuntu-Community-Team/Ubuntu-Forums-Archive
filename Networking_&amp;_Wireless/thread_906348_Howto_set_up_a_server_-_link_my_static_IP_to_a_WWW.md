---
title: "Howto set up a server - link my static IP to a WWW address (DNS question)"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by adhg on 2008-08-31
Hi experts,

I'm trying to setup a server where user on the WWW can actually go into my dummy page [www.showMeMyServer.com](www.showMeMyServer.com).

background:

1. I have a static IP and my server has apache. 
2. When you type the ip address [http://60.161.92.13](http://60.161.92.13) you get to see my dummy page: Hello World.html


Now, it's not friendly to refer my users to the ip address (the number) above so I purchased from yahoo the domain name: showMeMyServer.com


Question: How can I link the domain name to the IP address so 
[http://60.11.12.13](http://60.11.12.13)  =   [http://www.showMeMyServer.com](http://www.showMeMyServer.com)


thanks for any help.
adhg

* the IP and URL are just for the example ;-)
* I don't want to have a 'redirect'

---

### Post by tronica on 2008-08-31
Its pretty simple, you need to change the A record to point at your ip. I've never used yahoos control panel, so i found this to walk you through it.

[http://help.yahoo.com/l/us/yahoo/smallbusiness/domains/domainfeatures/advanceddns/advanceddns-05.html](http://help.yahoo.com/l/us/yahoo/smallbusiness/domains/domainfeatures/advanceddns/advanceddns-05.html)

---

### Post by adhg on 2008-09-08
YES! thank you!

---

