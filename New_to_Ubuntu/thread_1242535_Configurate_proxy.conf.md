---
title: "Configurate proxy.conf"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by MikeKat on 2009-08-17
There is Ubuntu 8.10 and Apache2 on it. Have installed and enabled module mod_proxy for using directive ProxyPass. Also have proxy.conf:
```

<IfModule mod_proxy.c>
        ProxyRequests Off
        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                Deny from all
        </Proxy>
        ProxyVia On
</IfModule>

```
And httpd.conf:
```

ProxyPass / http://Site1/
ProxyPassReverse / http://Site1/

```
When I try to request url ([http://ubuntu_ip/](http://ubuntu_ip/)) I receive error "403 Forbidden" - Ok. But when I change in proxy.conf "Deny from all" on "Allow from all" I receive "500 Internal Server Error". Tried a lot of variants - don't know what to do.
Thank you for help.

---

### Post by Shig on 2009-08-17
Hi

Have you run through all of the steps detailed [here?]("http://www.livingubuntu.com/77") Seems the module also has to be enabled for this to work in Ubuntu.

---

### Post by MikeKat on 2009-08-17
> **Shig said:**
> 
Have you run through all of the steps detailed [here?]("http://www.livingubuntu.com/77") 
Yes. I used this tutorial.

---

