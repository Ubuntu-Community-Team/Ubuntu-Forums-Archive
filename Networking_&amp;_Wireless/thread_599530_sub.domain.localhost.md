---
title: "sub.domain.localhost"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by zcox on 2007-11-01
I'm doing web development (LAMP) on Ubuntu 7.10.  To be able to develop locally, I do the following for each new site:
 - create a new site file in /etc/apache2/sites-available and do a2ensite on it
 - add a "127.0.0.1 site" line to /etc/hosts
 - create a new directory at ~/dev/site that is the document root for this site

This works great, as I can just type [http://site](http://site) in a browser and view my local version of the site.

For one site in particular, I need to test out user account subdomains, so I need to use URLs like [http://bob.site](http://bob.site), [http://phil.site](http://phil.site), etc.  But I can't seem to set up apache or /etc/hosts to support wildcard subdomains.

Any ideas on how to use wildcard subdomains on locally hosted sites?

---

