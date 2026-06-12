---
title: "remote accessing my LAMP server"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by roger99 on 2006-11-04
Hi,

I have a small LAN (two computers) one running ubuntu desktop one running ubuntu LAMP both behind a router so both have internet access.  I have designed a website for someone which is on the LAMP server, i can access the website on the internal network so I know it works.  What I would like to know is how someone (the person I have set the website up for) could access the website remotely so they can see the progress I have made.  Is this possible without using dynamic DNS.

---

### Post by quux on 2006-11-04
A dynamic DNS is not necessary... you can just tell the person your IP (which you can find using the management interface of your router or a service like e.g. [http://showmyip.com]("http://showmyip.com")).

Additionally you will most likely have to configure your router to forward incoming requests to your local server. This can typically be done in the management interface of your router (often called "port forwarding", "firewall rules", "services" or something like that). There you have to define a rule, that forwards all incoming TCP traffic on port 80 on the external interface of your router to port 80 of your internal HTTP server (or the port number you configured your internal server to listen on).

HTH

---

### Post by d.j.schroeder on 2006-11-04
You could just give the person your IP address.  It sounds like you have the machine connected to the router so you'll have to get the IP address from the router, or just go to [www.getip.com](www.getip.com) to get the address.  You'll also have to configure the router to forward port 80 to the LAMP server.

Of course when your IP address changes it won't work anymore.  I don't know what is typical but mine seems to stay constant for several days at a time, enough for someone to take a look.

---

### Post by roger99 on 2006-11-04
Err, simple as that. Thank you for the replies.

---

### Post by maximilian35 on 2006-11-07
Hey guys you can browse your web site by apache. Yes forward your ports 443 and 80 for apache accesing. 
Also you can have an account from [http://www.dyndns.com]("http://www.dyndns.com"). as dynamic ip. Then you have to download ddclient program. This program make an ip dedection everytime you access the net. Its configuraton file (ddclient.conf) is a little bit hard to configure but if you search you will find help for the ddclient configuration.

---

