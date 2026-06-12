---
title: "How do I install owncloud on pagekite"
date: 2013-12-07
forum: Networking &amp; Wireless
---

### Post by viralfilmsinc on 2013-12-07
Hello Everyone!

I just found out about this software called pagekite that enables a computer to be accessed anywhere easily, and I've been trying to develop an owncloud server to backup to, but I couldn't figure out where to place the extracted owncloud folder to get it to work w/pagekite....so then I tried 

```
sudo apt-get install owncloud
```

...but then when I opened the link to the website I made, I got an error saying it didn't have permission to edit the owncloud config file. I've been rummaging through the internet for hours and I haven't gotten what I wanted. Does anyone know how to install owncloud on pagekite?

---

### Post by CharlesA on 2013-12-07
Read here:
[http://doc.owncloud.org/server/5.0/admin_manual/installation/installation_linux.html](http://doc.owncloud.org/server/5.0/admin_manual/installation/installation_linux.html)

---

### Post by viralfilmsinc on 2013-12-07
I went to this...and I didn't get. I don't have a /srv/www/htdocs folder. I just have pagekite, owncloud zip folder, and lampp.

---

### Post by CharlesA on 2013-12-07
You should be able to install ownCloud just like you would normally. I don't think pagekite would mess with anything as it is just a way to access your server remotely.

Are you trying to serve anything else via Apache? If so, use the same configuration for owncloud.

Question: Is this a home server or a VPS that you have? Unless you have a dynamic IP and port 80 (and 443) is blocked, the only thing I think pagekite adds is an extra layer you need to figure out to get things working.

---

