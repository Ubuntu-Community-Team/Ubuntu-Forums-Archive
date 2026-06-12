---
title: "How to do a host header redirect on ubuntu?"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by edmicman on 2007-05-09
I'm running Ubuntu Server 7.04, installed with the LAMP setup.  I'm setting up Bugzilla 3.0rc1, and it is actually working great.  The server name is set to 'ubuntulinux'.

I'm on an SBS2003 domain, and would like to be able to type in a browser address bar 'bugs.ubuntulinux' and have it redirect to the bugzilla directory.  Currently, to get to bugzilla I have to go to [http://ubuntulinux/bugs](http://ubuntulinux/bugs) to get to it.  I have the DNS set up so that 'bugs.ubuntulinux' goes to IP address of the server, but how do I configure Apache to in turn redirect to the bugs folder?  Sort of like the IIS host headers thing.  

I'm still learning the ins and outs of this here, so I'm sure it's in a file config somewhere, but I just can't seem to find it.  Any help would be awesome - thanks!!

---

### Post by dante.regis on 2007-05-09
The config file, definetely is /etc/apache2/sites-enabled/(theres probably only one file there)

I really don't remember how to set it up, but good places to look would be on the Apache documentation about VirtualHost, mod_rewrite, Alias and things like that. Go to [http://httpd.apache.org]("http://httpd.apache.org") to find the docs.

---

