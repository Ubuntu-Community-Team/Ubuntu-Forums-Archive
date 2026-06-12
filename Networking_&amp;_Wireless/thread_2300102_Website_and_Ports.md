---
title: "Website and Ports"
date: 2015-10-23
forum: Networking &amp; Wireless
---

### Post by ex-para on 2015-10-23
I have a one page website and I use Nginx on Ubuntu 12.4 lts. The computer is an old Toshiba laptop. I let my site laps for a few months now I need to use it again but since then I changed the hub to 
 a Bthomehub 5 and could not get the site online. I re-installed Nginx and as it is a one page site I again deleted the Welcome to Nginx and replaced this with my site details. All this went OK and my site came up on local host but not on the net. Maybe this is to do with the port. Homehub 5 has automatic smart selection something or other so I thought before I go into the port situation I would ask the advice of this forum.

---

### Post by SeijiSensei on 2015-10-23
Some providers block inbound port 80 on their routers to enforce the "no-servers" clause in their Terms of Service.  Have you read yours? 

BT is not on this list of ISPs that allow servers: [http://www.dslwebserver.com/main/fr_index.html?/main/isp-hot-list.html](http://www.dslwebserver.com/main/fr_index.html?/main/isp-hot-list.html)

---

### Post by ex-para on 2015-10-23
No but I had BT previously and on this one there is a drop down list of items that can connect and the Web is one of them same as before.
Thanks for the reply.

---

### Post by howefield on 2015-10-23
You should be ok, I do the same with the same provider and the same Home Hub 5.

Sounds like you know what to do.

---

### Post by ex-para on 2015-10-23
Thanks, but that is it I don&#8217;t know as I am stuck with the port problem if that is my problem.

---

### Post by ex-para on 2015-10-23
Thanks, but that is it I don’t know as I am stuck with the port problem if that is my problem.

---

### Post by ex-para on 2015-10-25
So that must be what i get. Thanks again for the replies.

---

### Post by ex-para on 2015-10-31
I&#8217;m here again after a lot of trial an error I have got the port thing sorted and can see Welcome to Nginx in local-host. BTHH 5 is different to other versions and so is the version of Nginx. With the last version I could use this ( gksudo gedit /var/www/nginx-default/index.html )to place details of my site on the page where Welcome to Ngnix was. After installing the new Nginx version the path is now ( usr/share/nginx/www/index.html ) this can get the site to show on local host but not on the web. I do not know why this is, the only thing I have done nothing with is sites/enabled etc.. Please
what do I do now as I have port 80 open. 
l

---

