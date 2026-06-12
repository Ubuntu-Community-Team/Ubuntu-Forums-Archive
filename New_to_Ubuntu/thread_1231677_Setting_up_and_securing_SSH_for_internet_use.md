---
title: "Setting up and securing SSH for internet use"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Alk1 on 2009-08-04
Hi

I am trying to setup and secure SSH on Ubuntu so that I can SSH into the Ubuntu machine from the internet when I am travelling about.

So far in the SSH config I have:
Changed the port to a custom port
Denied root logins
Removed Password Authentication

I have setup the keys and it works internally on the LAN (yet to test from the internet).

I have then setup a port forward on my router/firewall so that anything from the internet on the  custom port I set in SSH (eg. 22) gets forwarded to the LAN IP address of my Ubuntu machine on the same custom port I set in SSH (eg. 22).

Please can someone advise if there is anything else that needs doing to secure the SSH configuration on the Ubuntu box? 
and whether I have setup the port forward on my router correctly?

Secondly, is a firewall required on the Ubuntu box?

Many thanks,

---

### Post by Hobgoblin on 2009-08-04
> **Alk1 said:**
> 

Please can someone advise if there is anything else that needs doing to secure the SSH configuration on the Ubuntu box? 

Nope, that is as secure as you are going to get it.

> 
Secondly, is a firewall required on the Ubuntu box?


No, unless you know what IP addresses you will be using and want to limit access to those, even then you may as well do that on the router.

---

### Post by Alk1 on 2009-08-04
Hi

Thanks for your prompt reply.

No, I don't know about the source IP address I shall be using, so I just used port forwarding on the router and so I guess I don't need a firewall on the Ubuntu machine either from what you have said.

Thanks again for your help. :D

---

### Post by wojox on 2009-08-04
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

