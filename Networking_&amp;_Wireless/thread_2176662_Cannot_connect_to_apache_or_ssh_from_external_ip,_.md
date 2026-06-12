---
title: "Cannot connect to apache or ssh from external ip, but can connect to tomcat"
date: 2013-09-25
forum: Networking &amp; Wireless
---

### Post by robert39 on 2013-09-25
I have Ubuntu server 12.04 running in VMware player on a Vista laptop connected to the internet through wifi to a netgear router. Port forwarding is set up on the router for ports 80 (apache), 8080(tomcat) and 22 (ssh). Tomcat is serving up pages just fine, but apache and ssh are invisible from the world outside. 

I have tried messing with /etc/hosts and with /etc/apache2/ports.conf to no avail.

The only difference I can find is that "netstat -plnt" shows apache and ssh listening on 0.0.0.0:80 and 0.0.0.0:22 respectively, but tomcat's listening on :::8080.

I'm stuck. Help?

Thanks massively.

---

### Post by sanderj on 2013-09-25
My guess: your netgear is reserving 22 and 80 for itself. First test: redirect incoming Internet traffic on 8765 to your webserver port 80.

---

### Post by robert39 on 2013-09-26
Thanks heaps for the reply. The router's web interface won't let me route ports. You can redirect only to IPs.

I solved the problem though by setting apache to listen to another port (8010) and set the router accordingly.

---

