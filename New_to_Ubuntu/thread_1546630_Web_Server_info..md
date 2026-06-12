---
title: "Web Server info."
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Tnoty on 2010-08-05
Can I use a single Linux server to support multiple web site domains and if so, is there a limit to how many?

---

### Post by 0004tom on 2010-08-05
Yep, Nope.

You should read up on VirtualHosts.

---

### Post by Tnoty on 2010-08-05
Know any good links to read up on VirtualHosts?

---

### Post by 0004tom on 2010-08-05
Well it's all dependent one which webserver you've decided to go with, as there are quite a few, apache, lighttpd etc etc, and all are different. In terms of config files and such.

---

### Post by Tnoty on 2010-08-05
Apache 2

---

### Post by DanYoSon on 2010-08-05
If you haven't read the apache documentation on virtual hosts it is here

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

---

### Post by sandyd on 2010-08-05
```

wget -c http://cdnetworks-us-1.dl.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb
sudo dpkg -i webmin_1.510-2_all.deb
sudo apt-get -f install
sudo mkdir /etc/init.d-dangerous
sudo mv /etc/init.d/webmin /etc/init.d-dangerous
sudo ln /etc/init.d-dangerous/webmin /usr/bin/webmin-control
sudo webmin-control start

```that should give you a web interface to create virtual hosts.
For security reasons, I have disabled webmin by default.
Whenever you want to use it, run
```

sudo webmin-control start
```
before using it.

go to [https://localhost:10000](https://localhost:10000)

login with your username and password.

Click on "servers" -> apache web server.
from then on, its quite self explanatory...

---

### Post by cjtemple on 2010-08-05
A word of caution if you use Webmin. Do not open the port outside your network. Hackers love Webmin since it can execute commands as root.

---

### Post by christopherjoel on 2010-10-06
@cjtemple - If my server isn't on the local network, then how would I access Webmin without opening the port?  I can already SSH into the server, but some things are simpler when done via GUI...

---

