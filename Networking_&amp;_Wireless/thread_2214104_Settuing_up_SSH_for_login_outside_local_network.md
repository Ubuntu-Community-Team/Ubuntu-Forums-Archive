---
title: "Settuing up SSH for login outside local network"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by llewellynpienaar on 2014-03-30
Good day Dear Ubuntu community. 


I am fairly new to linux server and systems but I do work on linux servers on a daily basis for work. I just never had to set one up from scratch.

I have a DDNS name that I would like to use to ssh to my linux server at home. Internally I can access my linux server via putty from windows using the local IP. I cant ssh to my linux machine using the hostname "server1" that is set to my machine, but I am not bothered about that.

What I would like to do is log in to my linux server when I am not home using "mydnsname.com" to login to my server. I know I can set up ipfire or any other firewall to set up my dns name and to forward the ports etc. so that when i ssh to mydnsname.com:22 it will direct me to 0.0.0.0:22 (local ip).

I know this can be done on the linux server itself. 

My server dails out via the router which is in bridge mode. I set up ppp0 via ppp0config comand which helps you to set up ppp0 connection. Just to give more clarity. I am using ubuntu server 12.10.

Please ask for any other information that might help in this regard. 

Ps. I spent a whole day searching for solutions on other forums and the ones with a similar issue or request as my situation was not answered. the thread just ended.

Thanks.
Esgaroth

---

### Post by Lars Noodén on 2014-03-30
The modem itself usually supports dynamic DNS service.  Somewhere there in the modem's administration interface is a form where you enter the service, the account name and password.  Then whenever you turn on the modem, it will update the DNS entry.  You can do that instead on your server with the package ddclient but then you might not always be in sync with your modem.  You'd have to run it manually if your modem got turned off and on and the home server didn't.  But if that is in bridge mode maybe that is what you need.

Once that is working you can turn on port forwarding on the modem to forward to your server, if bridge mode does not have that covered.

---

### Post by llewellynpienaar on 2014-03-31
Hey Lars. 

Thanks for the help. The issue was I had a hostname but I changed the prefix just before setting up remote access and forgot about the changes I made :P
The noob in my is stronk yesterday. 

Regards

---

### Post by PartisanEntity on 2014-03-31
*Moved thread to Networking & Wireless.*

---

