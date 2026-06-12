---
title: "Can't get to websites on my server after upgrade"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by jrtboht on 2011-02-03
I set up a webserver and had everything working great the last few months until I decided to install postfix, ispconfig, squirrelmail and other things included in the Perfect Server guides yesterday.  The installs went fine and I decided while I was at it I would upgrade from 10.04 to 10.10 (that seemed to go fine also).  However, now I can't access my websites.  I get a 403 error

**Forbidden**

 You don't have permission to access /annarankings.com/ on this server.


I tried accessing through [www.annarrankings.com]("http://www.annarrankings.com") and 71.114.220.3/annarrankings.com and get the same error.  I tried setting up the site in ispconfig but still couldn't get anything.  I noticed in the "sites-enabled" folders that the document root was /annarrankings.com/web so I added a simple "hello world" index.php in that location but still got the same error.  Here's my error log (at least a small portion of it)


```
[Thu Feb 03 09:12:34 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined variable: wb in /usr/local/ispconfig/interface/lib/app.inc.php on line 18$
[Thu Feb 03 09:12:36 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined index: domain in /usr/local/ispconfig/interface/web/sites/web_domain_edit$
[Thu Feb 03 09:12:36 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined index: on_after_update in /usr/local/ispconfig/interface/lib/classes/plug$
[Thu Feb 03 09:12:36 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined index: sites:on_after_update in /usr/local/ispconfig/interface/lib/classe$
[Thu Feb 03 09:12:36 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined index: sites:web_domain:on_after_update in /usr/local/ispconfig/interface$
[Thu Feb 03 09:12:36 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined variable: wb in /usr/local/ispconfig/interface/lib/app.inc.php on line 18$
[Thu Feb 03 09:12:37 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined index: domain in /usr/local/ispconfig/interface/web/sites/web_domain_edit$
[Thu Feb 03 09:12:37 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined index: on_after_update in /usr/local/ispconfig/interface/lib/classes/plug$
[Thu Feb 03 09:12:37 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined index: sites:on_after_update in /usr/local/ispconfig/interface/lib/classe$
[Thu Feb 03 09:12:37 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined index: sites:web_domain:on_after_update in /usr/local/ispconfig/interface$
[Thu Feb 03 09:12:37 2011] [error] [client 192.168.1.47] PHP Notice:  Undefined variable: wb in /usr/local/ispconfig/interface/lib/app.inc.php on line 18$
[Thu Feb 03 09:13:01 2011] [notice] Graceful restart requested, doing restart
Warning: DocumentRoot [/var/www/annarrankings.com/web] does not exist
[Thu Feb 03 09:13:02 2011] [notice] Digest: generating secret for digest authentication ...
[Thu Feb 03 09:13:02 2011] [notice] Digest: done
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/php_mcrypt.so' - /usr/lib/php5/20090626+lfs/php_mcrypt.so: cannot o$
[Thu Feb 03 09:13:03 2011] [notice] Apache/2.2.16 (Ubuntu) DAV/2 mod_fcgid/2.3.5 mod_ruby/1.2.6 Ruby/1.8.7(2010-06-23) mod_ssl/2.2.16 OpenSSL/0.9.8o conf$
[Thu Feb 03 09:13:03 2011] [warn] long lost child came home! (pid 2851)
[Thu Feb 03 09:14:59 2011] [error] [client 192.168.1.47] client denied by server configuration: /var/www/annarrankings.com/
```Any help would be greatly appreciated.

---

### Post by cariboo on 2011-02-03
Did you get your problem fixed, as I can access [http://www.annarrankings.com/]("http://www.annarrankings.com/") from here.

---

### Post by jrtboht on 2011-02-03
I uninstalled ispconfig, deleted all sites in sites-available and sites-enabled.  Then readded my sites to the sites-available folder and manually and create and symbolic link in site-enabled to each file in sites-available.  This seems to have got me back up and running.  I'm just going to forget about ispconfig and do things this way.

---

