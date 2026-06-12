---
title: "proxy"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by re-entity on 2007-01-20
My install of Ubuntu was performed on a machine at my office where we have a proxy. I'm now at home where there is no proxy. 

Using sudo apt-get update or Package Manager gives me the following error message:
E: Syntax error /etc/apt/apt.conf.d/20proxy:1: Unsupported directive '#Acquire::http::Proxy'

My config file: /etc/apt/apt.conf is empty.

The proxy settings in the file /etc/apt/apt.conf.d/20proxy are commented.

How do I get these services back online?

---

### Post by public_void on 2007-01-20
Before trying anything make a backup by copying the file.
```
cp  /etc/apt/apt.conf.d/20proxy /etc/apt/apt.conf.d/20proxy.backup
```
Then try removing the lines completely, or delete the file.

---

### Post by bapoumba on 2007-01-20
Hi,
```
~ $ cat /etc/apt/apt.conf
ACQUIRE {http:: proxy "direct"};

```

Here is the correct syntax for apt.conf without a proxy (please remove the space between http:: and proxy as :+p is a smiley ;)).
My laptop gets connected at work with a proxy and at home without. I sometimes have to run the update several times for aptitude to pick up the new config (I have not looked into that).
Make sure that there is no global proxy set up (> System > Preferences > Network Proxy) and that /etc/environment is also clear from any proxy entries.

---

### Post by re-entity on 2007-01-20
Thanks, I deleted it...it works now!

Cheers!

---

### Post by rrod on 2007-05-28
> **bapoumba said:**
> Hi,
```
~ $ cat /etc/apt/apt.conf
ACQUIRE {http:: proxy "direct"};

```

Here is the correct syntax for apt.conf without a proxy (please remove the space between http:: and proxy as :+p is a smiley ;)).
My laptop gets connected at work with a proxy and at home without. I sometimes have to run the update several times for aptitude to pick up the new config (I have not looked into that).
Make sure that there is no global proxy set up (> System > Preferences > Network Proxy) and that /etc/environment is also clear from any proxy entries.

[COLOR="DeepSkyBlue"]_____________________[/COLOR]

[B]Hello bapoumba!   :)

  I was looking for the correct syntax for apt.conf without a proxy. And I saw your PM.
Your suggestion was exactly the solution that I was looking for. !!!

Thanks a lot !!! . I did the changes at my server, and now It works very good!!!

Again:  THANK YOU !!!!!  :D :D ;)


Greetings from Costa Rica,[/B]


:KS   * * *  **Rose**   ;)

---

