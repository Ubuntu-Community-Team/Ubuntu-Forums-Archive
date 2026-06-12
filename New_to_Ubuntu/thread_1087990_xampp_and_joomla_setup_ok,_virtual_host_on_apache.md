---
title: "xampp and joomla setup ok, virtual host on apache?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by rogasgr on 2009-03-05
hello

since i started using ubuntu i want to learn more and more and i  now try to setup a web server for joomla. i setup xampp and joomla with success. now my webpage for [http://localhost](http://localhost) is xampp page. i have a joomla site on [http://localhost/xxxxx](http://localhost/xxxxx) which is ok. i also setup no-ip on my adsl router (dynamic IP) and forwarded the port 8080 to internal ip:80 with success. 

so now when a friend hits the [http://xxxxx.no-ip.info](http://xxxxx.no-ip.info) from the internet he gets the xampp page. 

how do i configure the [http://localhost/xxxx](http://localhost/xxxx)   to be my default site?

i founded info about declaring virtual host in httpd.conf but my /etc/apache2/httpd.conf is a blank file!   :(

---

### Post by Xiong Chiamiov on 2009-03-07
> **rogasgr said:**
> 
i founded info about declaring virtual host in httpd.conf but my /etc/apache2/httpd.conf is a blank file!   :(
If it was, Apache wouldn't be running.  You're probably mispelling the name and thus creating a new file (use tab-completion instead of typing out the full path).

Apache has [very excellent documentation](http://httpd.apache.org/docs/2.0/vhosts/examples.html).

XAMPP is not designed for production servers.  If you're opening it up to the web, you should use real Apache (or lighttpd, or nginx) instead.

---

