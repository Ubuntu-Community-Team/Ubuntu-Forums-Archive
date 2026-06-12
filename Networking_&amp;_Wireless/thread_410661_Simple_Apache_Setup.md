---
title: "Simple Apache Setup"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by jef0509 on 2007-04-16
I am a new linux user.  I am trying to setup a webserver (amoung other things) to run apache2 and mongrel for a website that is on ruby on rails.

I have successfully installed everything.  The server is running mongrel on port 3000.

I am trying to configure apache2 to send the traffic from my domain name (jeffburke.homelinux.com) to my mongrel process running on port 3000.

Right now I just get the apache2 index page.  If I go directly to jeffburke.homelinux.com:3000, I get the page I desired.

I followed this [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails) guide.  I tried the apache2 + fcgi install at the bottom but still no luck.  I still get the apache2 default page.

I imagine this is a real easy problem to fix and I am just doing something dumb.

Thanks for any help in advance.

---

### Post by hasimir44 on 2007-06-21
I just installed apache2, rails, mongrel, etc..  I'm still looking into how to forward from apache to mongrel, however, at this stage in my exploring I'm not exactly sure why I'd want to have 2 http services running.. I'm sure I just haven't read far enough yet :)

I stopped apache and started mongrel on port 80 which works for now.. 

```

sudo /etc/init.d/apache2 stop
sudo mongrel_rails start -p 80
```

I'll keep looking and post how to get them to play together later - unless someone else is nice enough to beat me to it..

---

