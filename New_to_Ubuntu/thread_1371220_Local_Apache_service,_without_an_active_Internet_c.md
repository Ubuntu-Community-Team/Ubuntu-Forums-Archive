---
title: "Local Apache service, without an active Internet connection."
date: 2010-01-03
forum: New to Ubuntu
---

### Post by The Other Steve on 2010-01-03
Hello.

I installed LAMP following the Community Documentation page, and the service seems to work correctly -- if (and only if) I have an active Internet connection.  I'd like to run the service just locally, for development and testing, and not have to have an active Internet connection just to do that.  Without an active connection, Apache responds with "failed to set up sockaddr".

I saw what I think is exactly this issue discussed on another forum, but (frustratingly) I haven't been able to successfully implement the proposed solution. :(  So, I thought I had better ask for help before I did something *really* stupid. 

Here is a clip from that thread, with the proposed solution:

> Permissions was not an issue. I was starting Apache as root, and wanted it to start on-boot. However, I fixed the problem.

I changed both the httpd.conf file and the ssl config file to both listen for *:80. This solved the problem. I think they just needed to both be listening for the same port with the same address format. Thanks for the suggestions, though...I tried adding a LISTEN 127.0.0.1:80 line to both those files.  The result was Apache would not start.  :(

---

### Post by 0cton on 2010-01-03
you don't add the line, the line should already be there usually withing the first lines of the config file (after the comments)
It is usually Listen port
you can modify it to Listen address:port
edit: I think his suggestion was to change it to Listen *:80
* as all.

---

### Post by The Other Steve on 2010-01-03
Hi.  Thanks very much for your reply and help.

I'm afraid it's my ignorance with respect to configuring Apache, but when I thought about it, it seemed to me that inserting a wildcard "*" into the server configuration wasn't such a good idea.  Though my intention is to use Apache strictly offline, it's easy to forget, and a wildcard seems like an invitation to a security disaster.  But I honestly don't know, which is why I thought I should ask for help _before_ I did something like it.

I'm trying to read some Apache documentation, but there's so much to learn.

---

### Post by tgalati4 on 2010-01-03
Well, depending on your internet connection, you can simply put a block on port 80 on your router then use apache on your LAN without external access.

When your website is ready to be exposed to the outside, you simply reinstate port-forwarding on port 80.

---

### Post by bodhi.zazen on 2010-01-04
You add that to /etc/apache2/ports.conf

[https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache](https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache)

Change the listen line to 

```
Listen 127.0.0.1:80
```

Then restart apache

```
sudo service apache2 restart
```

---

### Post by The Other Steve on 2010-01-04
Thank you for your replies.

The issue was not so much security, but the active connection.  Typically, I work at a desktop with an active connection, but I'd also like to be able to work in a (quiet, sunny) area of my home that has no internet service.  That's an issue because I can't seem to start Apache without an active internet connection.  I get the "failed sockaddr".  Active internet connection, no problems.

I did indeed make the change to the LISTEN line in ports.conf, as given in the Community Documentation page for LAMP.  That's ideal from the standpoint of security and local service only.  It doesn't resolve this requirement of an active internet connection, though.  Unfortunately.  Or, I haven't understood it.  :(

---

### Post by The Other Steve on 2010-01-04
Alright, I have managed to get what I wanted, but with a different set-up.  

I uninstalled LAMP and installed XAMPP (not in the repository), but an install guide here: [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410) .  XAMPP works just fine without an active internet connection.  So, ideal.  I feel a bit bad about this as a solution to my issue, as it seems such a gross "sledgehammer for a fly" solution, and I never actually understood what was wrong in the first place.  :(  Anyway, got what I wanted, and XAMPP is nice.

Thank you all, again, for your help.

---

