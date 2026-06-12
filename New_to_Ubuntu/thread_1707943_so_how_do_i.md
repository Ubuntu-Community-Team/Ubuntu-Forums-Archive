---
title: "so how do i"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by zachery on 2011-03-16
ok guys i got my apache2 server all setup and what not but how do i set it up so that other people can access it? I know i need a domain name but i tryed to register for a cc.co and it wouldnt let me use my ip address so im not sure how to go about it :(

any help would be awesome!


thanks!

---

### Post by crispy_420 on 2011-03-16
Looking for a free option depending on your router? Sounds like for casual use right? How comfortable are you with your routers settings.

Many routers support some sort of dynamic dns service. So you pick one and setup your account with them. Then fill in the appropriate settings within the routers settings page related to this account. Almost done. Next just enable the relevant ports to be forwarded to your machine, 80 (http) and if needed 443 (https). Also to save some later heartache, reserve your IP address to the server. Now just test it.

Kind of brief but on the right track?

---

### Post by zachery on 2011-03-16
> **crispy_420 said:**
> Looking for a free option depending on your router? Sounds like for casual use right? How comfortable are you with your routers settings.

Many routers support some sort of dynamic dns service. So you pick one and setup your account with them. Then fill in the appropriate settings within the routers settings page related to this account. Almost done. Next just enable the relevant ports to be forwarded to your machine, 80 (http) and if needed 443 (https). Also to save some later heartache, reserve your IP address to the server. Now just test it.

Kind of brief but on the right track?


i suck at router configs lol i have a WRT54GS

---

### Post by Bucky Ball on 2011-03-16
Please use descriptive thread titles. You will get more help that way from people who have an idea about your problem. Many experienced users will skip over 'So how do I ...'

It will help us help you. ;)

---

### Post by gandaran on 2011-03-16
> **zachery said:**
> i suck at router configs lol i have a WRT54GS
if your router doesn't support ddns you can still install a ddns client from software package manager and configure it to register with your free dns account.

---

### Post by ikt on 2011-03-16
> **zachery said:**
> any help would be awesome!

Why are you setting up an apache2 server?

If you want to host a website I would recommend going with a regular hosting package from a local web host, they take care of everything so you just have to upload your files.

---

### Post by mikewhatever on 2011-03-16
you don't ;)

---

### Post by crispy_420 on 2011-03-16
Even with a DNS client on the PC port forwarding would need to be enabled. And all this router stuff is actually easy. If you managed to setup your wireless you can do the other tasks mentioned. 

Here is the guide to port forwarding for your model: [http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/)

And the dynamic dns guide:
[http://geekswithblogs.net/saifkhan/archive/2008/12/29/setup-dyndns-dynamic-dns-on-a-linksys-wrt54g-router-again.aspx](http://geekswithblogs.net/saifkhan/archive/2008/12/29/setup-dyndns-dynamic-dns-on-a-linksys-wrt54g-router-again.aspx)

---

### Post by zachery on 2011-03-16
i got it figured out guys! thanks to all that helped i appreciate it and will take all the advice here thanks!

---

### Post by wep940 on 2011-03-16
Maybe you could post what you did to get this working for the rest of us who have never done it?

---

### Post by Bucky Ball on 2011-03-17
> **wep940 said:**
> Maybe you could post what you did to get this working for the rest of us who have never done it?

+1. That's what it's all about. ;)

---

