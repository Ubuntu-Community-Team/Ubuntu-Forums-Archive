---
title: "Hosting a web page on my home linux server?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by powel212 on 2009-02-06
Can I host a public web page on my home Ubuntu server box? 

for example I make a web page and put it on my server box, then people can navigate to [www.myhomeserverwebpage.com](www.myhomeserverwebpage.com) and arrive at my page.

If anybody knows any way to do this or a tutorial site on setting a public web page from a home server please let me know.

Basically I just want to host my own webpage/blog.

Thanks

Powel

---

### Post by Voland on 2009-02-06
Please check - [http://linux-blog.org/host-your-own-domain-and-webserver-using-apache/](http://linux-blog.org/host-your-own-domain-and-webserver-using-apache/)

---

### Post by kyeh on 2009-02-06
You need would to install LAMP (Linux, Apache, mysql, PHP)

I followed this guide to set my webserver [http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100)

If you are behind a router be sure to port forward ports 80 and 443 (apache default ports), some ISP's block 80 so you'll have to port forward another port. The ports used by apache can be changed via the file /etc/apache2/ports.conf

---

### Post by igknighted on 2009-02-06
> **kyeh said:**
> You need would to install LAMP (Linux, Apache, mysql, PHP)

I followed this guide to set my webserver [http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100)

If you are behind a router be sure to port forward ports 80 and 443 (apache default ports), some ISP's block 80 so you'll have to port forward another port. The ports used by apache can be changed via the file /etc/apache2/ports.conf

If you just want to put up some simple html/xhtml/css pages, there's no need for MySQL or PHP.

@OP: Configuring your computer is not the hard part, that is really straight forward.  The problem for you will be twofold.  (1) if you have a router, you need to forward the relevant ports (typically 80) to the proper machine, and (2) you need to find a way to get your domain name (usually a $10/yr investment) to point to your IP address.  The problem with #2 is that almost all home connections are on a dynamic IP, so you need to jump through some hoops to have your computer keep the DNS server up to date as to your current IP.

If you want to do this as a project to learn, go for it.  It's a lot of fun, I ran my own server for a few years in college.  But if you really just want to have a website, check out a free hosting site such as [http://www.freehostia.com](http://www.freehostia.com).  I use this to host my website now, it's much less hassle, more uptime, and lets me just focus on my design work.

---

### Post by powel212 on 2009-02-06
Wow! Great info. Thank you.

Powel

---

### Post by mikechant on 2009-02-06
Note of caution: Some ISPs *do not allow* users with non-business packages to host public websites (i.e. it's a breach of the Terms of Service). Whether and how they enforce this or not is another matter though.

---

