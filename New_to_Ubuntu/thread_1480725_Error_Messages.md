---
title: "Error Messages"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by macmike on 2010-05-11
Ok, I put in the lines for Virtual Hosting. At the terminal I am getting an error message that that *:80 has no VirtualHost. Then online I get this error - 
**Not Found**

 The requested URL / was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at wilmingtoncoc.com Port 80

What is going on what do I need to do. Having trouble with Proftpd as well. Haven't been able to get where I can configure and set up a user account to get in. I also need to install WordPress.

Mike

---

### Post by semafor on 2010-05-12
If you add a virtual site to /etc/apache2/sites-available and configure it correctly, you have to enable it. This you can do by either symlinking the site in sites-available to sites-enabled, or simply by running the command
```
$ sudo a2ensite sitename
```

Reload apache to enable the site.

---

### Post by macmike on 2010-05-12
I did the sudo a2ensite wilmingtoncoc.com

I then dids sudo service apache2 restart 

Now get an error message that says Site wilmingtoncoc.com already enabled. 
then I get [warn] NameVirtualHost 69.*.*.*:80 has no VirtualHosts
[warn] NameVirtualHost 8:80 has no VirtualHosts
[warn] NameVirtualHost *:80 has no VirtualHosts

So what now. I thought restarting and reloading were the same thing. Maybe I missed something there?

---

