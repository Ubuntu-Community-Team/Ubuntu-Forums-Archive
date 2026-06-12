---
title: "forbidden error"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by rajchd on 2010-07-09
I have installed ubuntu 10.04 on a computer as per instructions given on this link [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2) and everything went on smoothly.  I am intending to use this server as intranet server for developing php sites as well as training sites for internal users.
 
Though when I configure a site using ispconfig3, It creates the site but shows error 403, forbidden, when I try to navigate to that site.  Though I can ftp and upload files to this site.

---

### Post by cariboo on 2010-07-09
Is the site enabled in /etc/apache2/sites-enabled? I would check to see if **Deny from All** is commented out in the site-enabled file.

---

### Post by rajchd on 2010-07-10
These are the contents of /etc/apache2/sites-enabled. site name is learn.it
 
```

" ============================================================================
" Netrw Directory Listing                                        (netrw v136)
"   /etc/apache2/sites-enabled
"   Sorted by      name
"   Sort sequence: [\/]$,\<core\%(\.\d\+\)\=\>,\.h$,\.c$,\.cpp$,*,\.o$,\.obj$,\.info$,\.swp$,\.bak$,\~$
"   Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:exec
" ============================================================================
../
000-apps.vhost@
000-default@
000-ispconfig.conf@
000-ispconfig.vhost@
learn.it.vhost@

```

---

### Post by rajchd on 2010-07-12
And here is the most recent entries from the /var/log/apache2/error.log
 
```

[Mon Jul 12 11:33:44 2010] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon Jul 12 11:33:44 2010] [notice] Apache/2.2.14 (Ubuntu) mod_fcgid/2.3.4 PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations
[Mon Jul 12 11:36:42 2010] [error] [client 192.168.100.103] File does not exist: /var/www/favicon.ico
[Mon Jul 12 11:36:50 2010] [error] [client 192.168.100.103] client denied by server configuration: /var/www/learn.it/test.php
[Mon Jul 12 11:37:23 2010] [error] [client 192.168.100.103] client denied by server configuration: /var/www/learn.it/test.php

```

---

### Post by rajchd on 2010-07-12
Warning messages when i restart the apache and directory structure.
 
```

[EMAIL="root@ubuntu:/var/www/learn.it"]root@ubuntu:/var/www/learn.it[/EMAIL]# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                        [Mon Jul 12 16:11:42 2010] [warn] NameVirtualHost 192.168.100.250:80 has no VirtualHosts
[Mon Jul 12 16:11:42 2010] [warn] NameVirtualHost 192.168.100.250:443 has no VirtualHosts
 ... waiting [Mon Jul 12 16:11:43 2010] [warn] NameVirtualHost 192.168.100.250:80 has no VirtualHosts
[Mon Jul 12 16:11:43 2010] [warn] NameVirtualHost 192.168.100.250:443 has no VirtualHosts
                                                                                                                                 [ OK ]
[EMAIL="root@ubuntu:/var/www/learn.it"]root@ubuntu:/var/www/learn.it[/EMAIL]# ls
cgi-bin  log  ssl  tmp  web
[EMAIL="root@ubuntu:/var/www/learn.it"]root@ubuntu:/var/www/learn.it[/EMAIL]# cd web
[EMAIL="root@ubuntu:/var/www/learn.it/web"]root@ubuntu:/var/www/learn.it/web[/EMAIL]# ls
error  favicon.ico  index.html  robots.txt  stats
[EMAIL="root@ubuntu:/var/www/learn.it/web"]root@ubuntu:/var/www/learn.it/web[/EMAIL]#


```

---

