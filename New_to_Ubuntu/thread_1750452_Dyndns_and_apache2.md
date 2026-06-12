---
title: "Dyndns and apache2"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by hakermania on 2011-05-05
I have installed apache2 and I can see it locally (i can see index.html locally via typing my local IP address to other local PCs)
I've also setup a dyndns account, but I don't know how to actually link each other.
Now, when I type
mydnsaccount.dyndns.org
what i get is the password prompt from my modem -_-
Apparently this seems to happen locally because using a proxy and typing the same address always results to a time out!

So, I have an index.html at /var/www/ and i can see it locally, how do i connect it with dyndns so as to see it from everywhere???

thank you!

---

### Post by ubudog on 2011-05-05
First, you have to install ddclient.
```
sudo apt-get install ddclient
```

During the configuration process, it will ask you for your DynDns account info.  After that, they will be linked.  Now, you should setup a static IP on the server, and configure your router to forward port 80 to that IP.  All set!  

PS: If you are going to use Ubuntu Desktop Edition as a server, I would recommend being extra tight on security.  Might want to follow this checklist:

[http://www.hermann-uwe.de/security/articles/securing-apache-checklist](http://www.hermann-uwe.de/security/articles/securing-apache-checklist)

---

### Post by hakermania on 2011-05-06
Thanks, finally some modem settings and a static local IP address solved the problem!

---

### Post by ubudog on 2011-05-06
Cool, glad you got it.  :-)

---

