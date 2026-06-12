---
title: "apache2 virtualhost setup"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Genesis427 on 2009-05-15
I am running Ubuntu 8.04 with apache2 running.
There are two sites hosted on this pc with a static ip.

I am able to see one site in the browser from Megaproxy.com using the static ip but not using "mysite.com".  The second site is not available.

I can view that same site from within our network (as well as from the webserver/host pc) from the browser using the cable modem's ip address.

I cannot get a ping from one of the free ping websites to our static ip.

Can anyone recommend where I start to look to solve this/these issue(s).
Or what addition information is needed to diagnose.

Thanks

---

### Post by spiderbatdad on 2009-05-15
For mutiple sites, you should have each name fully qualified and registered. The rest is handled in the vhost file, by creating multiple DocumentRoots. Something like:
```
<VirtualHost 10.1.2.3>
  DocumentRoot /www/vhost1
  ServerName  www.my-site.com
  </VirtualHost>

```

---

### Post by Genesis427 on 2009-05-18
Thanks for the reply.

Here's what my virtual.conf file looks like:

NameVirtualHost *

    <VirtualHost *>
    ServerName [www.mysite1.com](www.mysite1.com)
    DocumentRoot /var/www/mysite1
    </VirtualHost>

    <VirtualHost *>
    ServerName [www.mysite2.com](www.mysite2.com)
    DocumentRoot /var/www/mysite2
    </VirtualHost>

---

### Post by Celauran on 2009-05-18
Are you able to access mysite1.com and mysite2.com by URL from the host machine?

---

### Post by Genesis427 on 2009-05-18
NO, [http://www.mysite1.com](http://www.mysite1.com) or [http://www.mysite2.com](http://www.mysite2.com) do not load in the browser.

[http://localhost](http://localhost) loads in the browser as mysite1.com

We can ping the webserver at 10.1.10.xx (ip via cable modem)
But cannot ping the webserver at 70.91.xxx.xx (static ip)

---

### Post by Celauran on 2009-05-18
Well, let's get everything working internally first. One problem at a time, if you will.

Have you made sure to a2ensite both vhosts? Are they also in /etc/hosts?

---

### Post by Genesis427 on 2009-05-18
Yes, I have a2ensite both sites.

Here's my hosts file 

```

127.0.0.1	localhost
127.0.1.1	webserver-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Celauran on 2009-05-18
```
127.0.0.1    localhost    www.mysite1.com    www.mysite2.com
```
Should get you able to access sites locally by URL.

---

### Post by Genesis427 on 2009-05-18
thank you
you rock
I can view both sites from this webserver now.
(cannot see the sites from computers on the network here, via anonymous web surfing)

---

### Post by Celauran on 2009-05-18
Have you checked that port 80 is open in the firewall? Are you able to ping the host machine from other machines on the network?

---

### Post by Genesis427 on 2009-05-18
Yes, port 80 is not blocked,  confirmed by canyouseeme.org

Yes, we can ping this computer from the network computers.
(the webserver plugs directly into the cable modem separate from the networked computers)

---

### Post by Celauran on 2009-05-18
I have set up multiple virtual hosts on multiple machines, but have never needed to make them accessible to the outside, so I'm afraid I won't be much help from here on. [This page](http://httpd.apache.org/docs/2.0/vhosts/examples.html) seems to be what you're looking for, though.

---

### Post by Genesis427 on 2009-05-18
Thank you for all of your help.

Thanks for that reference page.

I think I have a dns issue to be resolved.

Thanks again.

---

