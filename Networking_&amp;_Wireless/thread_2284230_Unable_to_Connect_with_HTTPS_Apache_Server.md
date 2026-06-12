---
title: "Unable to Connect with HTTPS Apache Server"
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by tristan16 on 2015-06-27
I've been experimenting with Apache web server and just set up SSL for secure connections, but I'm having a problem with it. localhost works on HTTP and HTTPS, the local network IP works with HTTP and HTTPS, however, the public IP address only works with HTTP. If I try to connect to the public IP with the secure connection, I get an "Unable to Connect" error.

I followed this tutorial, and I'm positive I did everything: [https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)

Any suggestions on how to fix this?

---

### Post by SeijiSensei on 2015-06-28
Does the machine have a firewall?  Does it permit traffic on port 443?  If the machine is behind a router, did you permit traffic and set up port-forwarding for port 443?

When you make a request for HTTPS, does it appear in /var/log/apache2/access.log?

---

### Post by tristan16 on 2015-06-28
> **SeijiSensei said:**
> Does the machine have a firewall?  Does it permit traffic on port 443?  If the machine is behind a router, did you permit traffic and set up port-forwarding for port 443?

When you make a request for HTTPS, does it appear in /var/log/apache2/access.log?

Thanks for the quick reply. Once again I missed the obvious. Port-forwarding port 443 has everything working now.

---

