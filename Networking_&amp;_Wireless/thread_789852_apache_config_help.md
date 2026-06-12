---
title: "apache config help"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by Geran on 2008-05-10
Is it possible to configure apache to only answer to one IP address?

For example, making it accessible eth1(10.0.0.1) and not eth0(192.168.0.100)?

many thanks for help. I appreciate it.

---

### Post by nixscripter on 2008-05-11
I think you can do that with the "allow" directive in the file:

```

<Directory />
# other stuff here
    Order Deny,Allow
    Deny from all
    Allow from my.ip.here.
</Directory>

```
See the mod_access module for more info:
[http://httpd.apache.org/docs/1.3/mod/mod_access.html](http://httpd.apache.org/docs/1.3/mod/mod_access.html)

---

### Post by Geran on 2008-05-11
Maybe I put the lines you gave me in wrong, but after applying them I keep on getting the same message from my server telling me that I am not allowed to access these resources....

I wasn't looking for this, but more of a way to tell apache to only listen requests on one interface. Such that, apache would only listen to requests at all on eth1 and wouldn't even acknowledge requests on eth0.

Where do I go for that?

---

### Post by nixscripter on 2008-05-12
My mistake.

So you want to only allow connections **from the interface at ** 10.0.0.1? I thought you wantd to only allow connections **from the client at** 10.0.0.1.

In that case, I would suggest just using iptables to bounce the packets. Something like this should work, assuming your server will run on port 80:

```

sudo iptables -A INPUT -i **accept-iface** -p tcp --destination-port 80 -j ACCEPT
sudo iptables -A INPUT -i **reject-iface** -p tcp --destination-port 80 -j REJECT --reject-with tcp-reset

```

This will get them a "connection refused" message, which is what I assume you want

---

### Post by Monicker on 2008-05-12
You can change your Listen directive in ports.conf

Change from 

```
Listen 80
```

to

```
Listen 10.0.0.1:80
```

---

