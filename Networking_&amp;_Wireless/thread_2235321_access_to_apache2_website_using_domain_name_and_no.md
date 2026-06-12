---
title: "access to apache2 website using domain name and not server's IP"
date: 2014-07-20
forum: Networking &amp; Wireless
---

### Post by capitainabloc on 2014-07-20
as written in the title, I want to access to apache2 website using domain name only and not server's IP.
  I would like to get a error 403 when trying to access the website with the server's IP.
  How is it possible?
  thanks

---

### Post by TheFu on 2014-07-20
Make the default website return a 403.
User a vhost for the real domain.  I think you'll need to setup 2 vhosts 
* default
* [www.example.com](www.example.com)
Does that make sense?

---

### Post by capitainabloc on 2014-07-20
isn't there a solution by htaccess or apache2.conf?
I already managed to do this, but can't remember how!

---

### Post by TheFu on 2014-07-20
> **capitainabloc said:**
> isn't there a solution by htaccess or apache2.conf?
I already managed to do this, but can't remember how!

Not that I know about and not that google could find in 3 minutes of searching.
I know that having 2 name-based virtualhost WILL work, just make the "default" return 403.

Now, if you know specific IPs you want to block ... that can be done too, but that also needs either an IP-based virtual host or a name-based virtual host ... as far as I know.

With all that said, my apache-fu is old and weak. We switched to nginx about 4 yrs ago, but still have 1 box running apache internally (behind an nginx proxy).

---

### Post by capitainabloc on 2014-07-21
I don't want to block any specific IP (I use fail2ban for this), but I want to allow access to my website only with domain name.
I will dig mod_rewrite...

I'll try also the solution with 2 vhosts.

thanks

---

### Post by capitainabloc on 2014-07-21
I managed, with help of this thread: [http://serverfault.com/questions/511413/in-apache-how-do-i-disable-access-to-a-website-when-someone-only-uses-the-ip-ad](http://serverfault.com/questions/511413/in-apache-how-do-i-disable-access-to-a-website-when-someone-only-uses-the-ip-ad)

finally, I added this into /etc/apache2/sites-available/default.conf:

```
        <Directory /var/www/>

RewriteEngine On
RewriteCond %{HTTP_HOST} ^xx\.xx\.xx\.xx
RewriteRule ^(.*)$ - [F,L]

[...]
        </Directory>
```


Now, I have a 403 error when typing directly my IP adress, and I can access my website only by typing the domain name.

thanks all.

---

### Post by TheFu on 2014-07-21
Very cool solution!  Thanks for posting it!

---

