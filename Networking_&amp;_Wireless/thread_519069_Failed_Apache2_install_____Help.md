---
title: "Failed Apache2 install     Help?"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by ncwalker on 2007-08-06
I'm trying to install Apache.  It seems to have gotten missed on my Fiesty Server LAMP install.   When logged in as the root I type

apt-get install apache2

After reading package lists and building dependcy tree, reading state information, I say yes to continue I get

WARNING: The following packages cannot be authenticated!
  libpq5

I say yes anyway and get

Err: [http://security.ubuntu.com](http://security.ubuntu.com) fiesty-security/main libpq5 8.2.4-0ubuntu0.7.04
   Could not resolve security.ubuntu.com
Failed to fetch ... and so on.

I know I am doing something wrong.  Can anyone help?  many Thanks

---

### Post by ncwalker on 2007-08-07
I got it.

A friend helped me set up my DNS.

I typed 
```
sudo vi /etc/network/resolv.conf
```

and added these two lines just below the search some.domain.name line.

```
nameserver 208.67.220.220
nameserver 208.67.222.222
```
then I typed 

```
sudo /etc/init.d/dns-clean start
```

to  clear my DNS cache.

Thanks benanzo!:)

---

