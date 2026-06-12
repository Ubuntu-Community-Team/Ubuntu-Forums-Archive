---
title: "Lamp as localhost only"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by shadowalexia on 2009-11-30
Hi

I was wondering after you install apache php and mysql, how do you turn off all access exept for localhost. I followed this howto when i installed it [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp)

and thats it, the author of this did not mention how to run it as a localhost only.

---

### Post by rudy.b on 2009-12-01
To tell Apache to listen only to requests from localhost, change your /etc/apache2/ports.conf file to modify the Listen directive to include the IP address for localhost.  

E.g. change this:
```
Listen 80
```
to this:
```
Listen 127.0.0.1:80
```

Also, you could activate your firewall to block all requests on port 80, or whatever port you have Apache listening on.

---

### Post by shadowalexia on 2009-12-05
okay thanks

and just to make sure. if i ever wanted it to be accessible to the public i put in my ip that my isp gives me?

---

