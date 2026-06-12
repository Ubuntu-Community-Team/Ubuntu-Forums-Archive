---
title: "Trouble to set up a virtual host with apache2"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Bruno974 on 2010-07-09
Hi all,

I'm trying to set up a virtual host with apache2.
So I created this file:
/etc/apache2/sites-available/domain1.com

with this content:

```

<VirtualHost *:80>

  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin webmaster@domain1.com
  ServerName  domain1.com
  ServerAlias www.domain1.com


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.html
  DocumentRoot /home/demo/public_html/domain1.com/


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/demo/public_html/domain1.com/log/error.log
  CustomLog /home/demo/public_html/domain1.com/log/access.log combined

</VirtualHost>

```

I did type this command: sudo a2ensite domain1.com
I reloaded apache2: sudo /etc/init.d/apache2 reload
But when I enter [http://domain1.com](http://domain1.com) in my browser I got the following error message:
Oops! Google Chrome could not find domain1.com

what should I do ?
thanks

---

### Post by stmiller on 2010-07-09
That is not a valid registered domain. 

Are just putting in domain1.com as an example?

---

### Post by Bruno974 on 2010-07-10
I found out a solution. I edited the /etc/hosts file.
Indeed, domain1.com isn't a valid registered domain.
My purpose was to host several sites on my dev server. A best way is to attribute a different port for each one.

---

