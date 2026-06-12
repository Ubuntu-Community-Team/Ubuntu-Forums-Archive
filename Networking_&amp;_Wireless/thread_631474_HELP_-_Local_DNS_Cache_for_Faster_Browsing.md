---
title: "HELP - Local DNS Cache for Faster Browsing"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by praveenpious on 2007-12-04
I tried the steps outlined at [http://news.softpedia.com/news/Local-DNS-Cache-for-Faster-Browsing-43341.shtml](http://news.softpedia.com/news/Local-DNS-Cache-for-Faster-Browsing-43341.shtml)

The webpage provides us with step by step instructions on configuring dnsmasq in ubuntu. But its not working out (for me!!) The webpages dont load up. Now am back to Opendns. Am on a PPPoE connection working in bridged mode. 

Help me please

---

### Post by csat on 2007-12-04
The above link is dead so I couldn't even try it out.

---

### Post by ruibernardo on 2007-12-04
Here is one to do it: [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

---

### Post by praveenpious on 2007-12-04
The link which i had posted and which epimeteo had posted basically is the same procedure. I had tried both, but its not working. Please help me out :(

---

### Post by ruibernardo on 2007-12-04
That page worked for me.

The file /etc/dnsmasq.conf is very well commented, so maybe you have to change some options. Make a backup copy of the original dnsmasq.conf file so you can start over later.

Your problem could be related to to the kind of connection you have (bridged pppoe). Can't help you about it, don't have a connection of that kind, sorry.

Maybe someone with a modem can help you.

---

### Post by csat on 2007-12-04
> **epimeteo said:**
> Here is one to do it: [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

Thanks.  I will check it out.

---

### Post by praveenpious on 2007-12-04
@epimeteo Thanks for replying. Most of my pals are able to configure dnsmasq properly and they too are on pppoe bridged mode.

---

### Post by csat on 2007-12-05
> **epimeteo said:**
> That page worked for me.

.

The same here but I am behind a router and worked fine.

---

