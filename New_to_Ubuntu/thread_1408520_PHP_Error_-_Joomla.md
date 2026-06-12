---
title: "PHP Error - Joomla"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by Happybattles on 2010-02-16
Here's the error.


```
Warning: require_once(/var/www/test/includes/defines.php) [function.require-once]: failed to open stream: Permission denied in /var/www/test/index.php on line 21

Fatal error: require_once() [function.require]: Failed opening required '/var/www/test/includes/defines.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/test/index.php on line 21
```

All of the files are present.  I'm sure it's just that something small is missing or there's a component missing.  This is my first attempt on my new Ubuntu with running Joomla.  I have phpMyAdmin installed, and have the database created.  But, I can't even get to the installation script.

---

### Post by kanikilu on 2010-02-16
Looks like a permissions problem. List the contents and permissions of that test directory: ```
ls -l /var/www/test
```

---

### Post by Happybattles on 2010-02-16
```
chris@chris-desktop:~$ ls -l /var/www/test
total 252
drwx------ 11 chris chris  4096 2010-02-12 19:44 administrator
drwx------  2 chris chris  4096 2010-02-12 19:44 cache
-rwxrwxrwx  1 chris chris 97981 2009-11-13 11:09 CHANGELOG.php
drwx------ 13 chris chris  4096 2010-02-12 19:44 components
-rwxrwxrwx  1 chris chris  3409 2009-11-13 11:11 configuration.php-dist
-rwxrwxrwx  1 chris chris  1175 2009-11-13 11:11 COPYRIGHT.php
-rwxrwxrwx  1 chris chris 14894 2009-11-13 11:11 CREDITS.php
-rwxrwxrwx  1 chris chris  2771 2009-11-13 11:11 htaccess.txt
drwx------  6 chris chris  4096 2010-02-12 19:44 images
drwx------  8 chris chris  4096 2010-02-12 19:44 includes
-rwxrwxrwx  1 chris chris   591 2009-11-13 11:12 index2.php
-rwxr-xr-x  1 chris chris  2052 2009-11-13 11:12 index.php
drwx------  7 chris chris  4096 2010-02-12 19:44 installation
-rwxrwxrwx  1 chris chris  4344 2009-11-13 11:13 INSTALL.php
drwx------  4 chris chris  4096 2010-02-12 19:44 language
drwx------ 16 chris chris  4096 2010-02-12 19:44 libraries
-rwxrwxrwx  1 chris chris 17816 2009-11-13 11:16 LICENSE.php
-rwxrwxrwx  1 chris chris 27984 2009-11-13 11:16 LICENSES.php
drwx------  2 chris chris  4096 2010-02-12 19:44 logs
drwx------  3 chris chris  4096 2010-02-12 19:44 media
drwx------ 22 chris chris  4096 2010-02-12 19:44 modules
drwx------ 11 chris chris  4096 2010-02-12 19:45 plugins
-rwxrwxrwx  1 chris chris   304 2009-11-13 11:26 robots.txt
drwx------  6 chris chris  4096 2010-02-12 19:45 templates
drwx------  2 chris chris  4096 2010-02-12 19:45 tmp
drwx------  4 chris chris  4096 2010-02-12 19:45 xmlrpc
chris@chris-desktop:~$ 

```

---

### Post by kanikilu on 2010-02-16
I haven't used or installed Joomla, so it might have more specific permissions requirements in the instructions, however, I'm pretty sure everything needs to be, at the least, readable by everyone.

You can see, for instance that the "includes" directory is chmod 700, which means it's only readable by your account. It should probably be 755: ```
chmod -R 755 /var/www/test/includes
```

You could do the whole directory tree at once with: ```
chmod -R 755 /var/www/test
``` but certain files or directories may need to be world-writable for all I know, so check the Joomla docs on that...

---

### Post by Happybattles on 2010-02-16
HA!
Thank you!  Works!!
Send me a ballot and I'll vote you a pay raise.

---

