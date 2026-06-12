---
title: "intranet server name resolution"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by shreko on 2005-11-03
Hi guys,

This must be a dumb question, but I hope somebody will help me. I am trying to set up a intranet LAMP server. I have a windows network with domain and little linksys router/firewall. Now if I set up ubuntu server with static IP 192.168.1.202 and give it a name server2 other machines can access it through 192.168.1.202 but can not resolve name server2. What do I need to do in order to get other machines use [http://server2/phpmyadmin](http://server2/phpmyadmin) for example?

Thanks,

Shreko

---

### Post by suRoot on 2005-11-03
Is the router doing DNS, too?  Some of those routers allow you to make DNS entries - don't know if your model does.  Dig around the admin interface & see if you can do it.

Another way, if you've only got a couple hosts is to manually edit the hosts file.

On the linux box:

sudo echo 192.168.x.x winbox >> /etc/hosts

On the windows box, edit c:\windows(or winnt)\system32\drivers\etc\hosts & add a line:

192.168.x.x linuxbox

...where 192.168.x.x = the right addresses & winbox / linbox = the actual hostnames.

You may need to run ipconfig /flushdns on the windows box.

You could also do this the "right" way by setting up proper DNS / DHCP on one of your servers, but if you've only got a few hosts this is probably the quickest / easiest way.

---

