---
title: "run perl cgi's from 20 cgi-bin directories"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by dguido on 2008-06-15
I have a directory hierarchy that looks like this: /var/www/*/cgi-bin

I want any directory that looks like the above to execute the perl .pl files inside of them as a CGI. I'm not looking to use mod_perl.

Right now my sites-enabled/000-default looks like this:
[HTML]
...
<Directory />
Options +ExecCGI -Indexes FollowSymLinks
AllowOverride All
</Directory>

<Directory /var/www/>
Options Indexes FollowSymLinks Multiviews
AllowOverride All
Order allow,deny
Allow from all

<Directory "/var/www/*/cgi-bin">
AllowOverride None
Options +ExecCGI -Multiviews +SymLinksIfOwnerMatch
AddHandler cgi-script .pl
Order allow,deny
Allow from all
</Directory>
...
[/HTML]

I can go up to each of the individual .pl scripts and run perl on them and they run fine. They're all chmod 775. Yet none of them execute through my web browser. What am I doing wrong?

---

