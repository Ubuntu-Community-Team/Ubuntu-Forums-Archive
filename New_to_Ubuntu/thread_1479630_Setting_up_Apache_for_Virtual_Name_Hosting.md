---
title: "Setting up Apache for Virtual Name Hosting"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by macmike on 2010-05-10
Can some one tell me how to set up Virtual Name Hosting for these three sites.  

1. - [www.wilmingtoncoc.com](www.wilmingtoncoc.com) will want to set up WordPress for this one. Need to know how to set WordPress up as well or at least how to install it.
2. - [www.mikealrhughes.com](www.mikealrhughes.com) will want to ftp files to it since I will be using my Dreamweaver http files already made for that one.
3. - [www.biblematters.net](www.biblematters.net) will be wanting to set up mailman here as this one is a closed mailing list site. 

Any help about where to start will help. Also want to set up Webmin or some other control panel as well. I need to get to where I can do all this from remote location.

All help appreciated. 

Mike Hughes

---

### Post by sandyd on 2010-05-10
hey, at least you got the right idea!
I was already thinking of webmin when I saw the thread title lol.

anyways, so...
```

sudo apt-get install apache2
wget -c http://cdnetworks-us-2.dl.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb
sudo dpkg -i webmin_1.510-2_all.deb
sudo apt-get -f install

```That should get you started.

Browse to [https://your.server.ip.here:10000](https://your.server.ip.here:10000)

ignore the security warning.

login.

click on servers

click on apache.

bam. your at where you wanna be.

---

