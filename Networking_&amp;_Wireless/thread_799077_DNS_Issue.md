---
title: "DNS Issue"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Black Mage on 2008-05-18
I am having trouble setting up Bind9 DNS and I get this error:

```

root@webserver:/var/log# /etc/init.d/bind9 restart
 * Stopping domain name service... bind
rndc: connect failed: 127.0.0.1#953: connection refused
   ...fail!
 * Starting domain name service... bind
   ...fail!

```

And I get this error the /etc/logs/messages

```

May 18 17:50:05 webserver -- MARK --

```

On the router, I have my firewall the ports 53 and 953 opened up and pointg to 192.168.1.202 which is webserver. So what can my problem be?

---

### Post by garyedwardjohnston on 2008-05-18
LOL...cant help but I use:

[http://freedns.afraid.org/](http://freedns.afraid.org/)

---

