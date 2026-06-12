---
title: "My web server wont work!"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by gfunkera on 2009-05-10
when i change my links on my web server to loopback/127.0.0.1, the site works just fine..

when i replace loopback/127.0.0.1 with my IP address, the site stops working... i can still access it but even from the server computer its impossible to access any of the links when the IP is used.. i tried restarting the apache2 web server but that didnt seem to work..

what should i do?

---

### Post by Iowan on 2009-05-10
Verify */etc/apache2/ports.conf* does NOT contain the line:> Listen 127.0.0.1:80 The default line is just > Listen 80 You *might* edit that line to include your server address instead... but that assumes a static address (or static lease - which is how my server is set up).

---

### Post by superprash2003 on 2009-05-11
do you mean WAN ip or LAN Ip?

---

