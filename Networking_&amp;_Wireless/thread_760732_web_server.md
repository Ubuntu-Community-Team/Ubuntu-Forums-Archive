---
title: "web server"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by wenek18 on 2008-04-20
Dear All

I wish to build my own webserver and host my sites locally, at the moment am paying for a shared server.

I know how to use apache, however am getting confused on how to configure a dns server so that my websites will route to my server.

Awaiting your replies 

Thanks - Justin

---

### Post by CrazyGuy123 on 2008-04-20
There are quite a few things you need to set up:

1.  You need to install apache, configure it, and put some files on it.

2.  You need port forwarding in your router to forward port 80 to the computer running apache (this only applies if you're running it on a home PC behind a firewall)

3.  (optional)  You need to use a service like DynDns to set up dynamic dns.  Note that some home broadand connections have static IP's, in which case you can use pretty muh any DNS service.  Most domain registrars provide DNS free with the domain.

Note that if you don't do step 3, you should still be able to view your website from the outide world by doing [http://xx.xx.xx.xx/](http://xx.xx.xx.xx/), where the xx's are your internet connections internet address, which you can see by going here:  [http://checkip.dyndns.org/](http://checkip.dyndns.org/)

Note that that will only work from outside your home network.  The above method is useful to test you've setup steps 1and 2 correctly.

As far as setting up a dns server goes, generally unless you want to do something really advanced, you don't need one.  There are plenty of free dns services available, and they'll be more reliable than your single server.

---

### Post by wenek18 on 2008-04-21
Hi 

Ok grt thanks for your help, what would you suggest as a free dns server ?

Thanks again 
Justin

---

### Post by Aztek on 2008-04-21
dyndns.org (as mentioned above)

---

### Post by maddog39 on 2008-04-22
You basically just do:
```

sudo apt-get install apache2

```
And configure virtual hosts in apache which basically lets it route domains and such. There are several guides out their and its not exactly easy when hosting multiple domains on a single server. Especially in relation to DNS. This guide below shows you everything and how to do it, hope it helps.

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

