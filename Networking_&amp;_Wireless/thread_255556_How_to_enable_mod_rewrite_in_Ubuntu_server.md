---
title: "How to enable mod_rewrite in Ubuntu server??"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by zoon_unit on 2006-09-11
I'm trying to find the right way/file to enable mod_rewrite.  I know the typical place to do this is in httpd.conf, but of course Ubuntu has its own funky way of doing this with the mods-available and sites-available conf files.

What's the official way to enable mod_rewrite on Ubuntu?

---

### Post by tbonius on 2006-09-11
I assume you are talking about Apache2 directory structure for Ubuntu.  This is the new and modular way all distributions will be laying out their Apache2 server config.

Mod_rewrite is compiled in by default.  You can see it in the /etc/apache2/mods_available directory.  If you feel like making doubly sure that it is loaded then simply put the following directive into httpd.conf:

```
LoadModule mod_rewrite /usr/lib/apache2/modules/mod_rewrite.so

```
You can verify what modules are loaded with:

```
sudo apache2ctl -l

```

T

---

### Post by zoon_unit on 2006-09-11
I actually found the following command that did the trick:

```
a2enmode rewrite
```

---

### Post by StFS on 2006-09-21
And for future references, the "correct" way to define a new site (such as a new virtual host) is to create the definition in /etc/apache2/sites-available in its own file and then call: 
```
a2ensite conf_file_name
```
to enable it.

---

### Post by ookadoo on 2007-08-25
> **zoon_unit said:**
> I actually found the following command that did the trick:

```
a2enmode rewrite
```

The correct program name is a2enmod as in "apache2 enable module <module>":

```
a2enmod rewrite
```

---

### Post by Pekz0r on 2007-09-01
I'm also looking for a way to enable the rewrite mod to apache2.

i ran the commmand a2enmod rewrite and it said that the mod was addess successfully, but i can't see it in the list when i type: sudo apache2ctl -l

I've tried to make a rewirie rule to test but i'm not sure how to do it. This is what i've done: 
In apache2.conf:
```

<IfModule mod_rewrite.c>
RewriteEngine On
</IfModule>
```

In .htaccess (in var/www/mysite):
```

RewriteEngine on
RewriteRule /page/([0-9]+) /page.php?page=$1
```

It does not work. What have i done wrong?

---

### Post by wasert on 2007-09-04
I am having the same problem.

mod_rewrite is enabled
```
a2enmod rewrite
```

I edited my /etc/apache2/apache2.conf and added the following lines (following Plone's guide):
```

<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteRule ^/(.*) http://localhost:8080/$1 [P]
</IfModule>
```

I tried adding a very simple RewriteRule and still didn't work

---

### Post by Pekz0r on 2007-09-04
I've found out the solution!

Change AllowOverRide None in /etc/apache/sites-available/default to AllowOverRide All(or something else, but not None). Apache won't read the rewrite rules nor the .htaccess-files if AllowOverRide is set to None.

Hope that helps you too!

---

### Post by wasert on 2007-09-04
still doesn't work

:(

thanks for your help though

---

### Post by Pekz0r on 2007-09-04
Is mod_rewite in the list loaded modules in phpinfo()?

Try putning the rewrite rules in a -htaccess file, that works for me

---

### Post by wasert on 2007-09-04
I am not using PHP, but I try the following command, and mod_rewrite appears to be loaded.

```
$ sudo apache2 -M
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_worker_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 cgid_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 proxy_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 status_module (shared)
 jrun_module (shared)
Syntax OK
```

I tried your suggestion and I changed the following:
First, I changed the following line in /etc/apache2/sites-enabled/000-default
```
 DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                [COLOR="Red"]AllowOverride all[/COLOR]
        </Directory>
        <Directory /var/www/>
                Options FollowSymLinks 
                [COLOR="Red"]AllowOverride all[/COLOR]
                Order allow,deny
                allow from all
        </Directory>
```

And then, I placed a .htaccess file in /var/www with the following contents
```
$ cat .htaccess 
RewriteEngine On
RewriteRule ^/(.*) http://localhost:8080/$1 [P]

```

After restarting apache, mod_rewrite still doesn't do anything.

Thanks for your help

---

### Post by socceroos on 2007-10-22
I know this may sound silly. But try changing 'AllowOverride all' to 'AllowOverride All'.

I have known apache to be pedantic about this sort of thing before.

---

### Post by gorkau on 2007-10-25
I had the same problem and the AllowOverride All solution worked fine for me. Here is what I did:

1) sudo a2enmod rewrite
2) sudo gedit /etc/apache2/sites-enabled/000-default 
3) Change AllowOverride None to AllowOverride All
4) Restart Apache: sudo /etc/init.d/apache2 force-reload

And that's all!

---

### Post by Delphinus on 2007-12-02
I had to disable multiviews to get my .htaccess overrides working properly.

---

### Post by theolster on 2007-12-06
I could really do with some help on this too.  I'm trying to install Durpal on my server, which would work a lot better if mod_rewrite is enabled.

```
sudo apache2 -M
```returns this```
apache2: illegal option -- M
```
but this works (and shows that mod_rewrite is not included)
```
$ sudo apache2 -l
Compiled in modules:
  core.c
  mod_access.c
  mod_auth.c
  mod_log_config.c
  mod_logio.c
  mod_env.c
  mod_setenvif.c
  prefork.c
  http_core.c
  mod_mime.c
  mod_status.c
  mod_autoindex.c
  mod_negotiation.c
  mod_dir.c
  mod_alias.c
  mod_so.c

```
yet I also get this result```
$ a2enmod rewrite
This module is already enabled!
```
I'm very confused and could do with some help getting this to work!

---

### Post by adster101 on 2007-12-18
I was getting the same as above. But I amended the sites-enabled file to AllowOverride All and my .htaccess file started to work. 

He he, very good.

---

### Post by evilninjamaster on 2008-01-15
The **/etc/apache2/sites-enabled/000-default** edit worked for me, too, although I think only the 
```
<Directory /var/www/>
        Options FollowSymLinks 
[COLOR="Red"]        AllowOverride all[/COLOR]
        Order allow,deny
        allow from all
</Directory>
```
edit is necessary, not
```
<Directory />
        Options FollowSymLinks
        [COLOR="Red"]AllowOverride all[/COLOR]
</Directory>

```
One more thing: after a lot of jiggery-pokery (trying different things), I had erroneously put the **RewriteLog** tag in the **.htaccess** file, where it is not allowed. My apache error.log usefully prints out:
```
... [alert] [client 127.0.0.1] /var/www/.htaccess: RewriteLog not allowed here
```
I had to correct the problem (move the tag to apache2.conf) before mod_rewrite started working.
Looks like Apache will disable mod_rewrite if you have any similar errors, so it's worth checking your apache error.log.

---

### Post by mahalie on 2008-01-17
> **gorkau said:**
> I had the same problem and the AllowOverride All solution worked fine for me. Here is what I did:

1) sudo a2enmod rewrite
2) sudo gedit /etc/apache2/sites-enabled/000-default 
3) Change AllowOverride None to AllowOverride All
4) Restart Apache: sudo /etc/init.d/apache2 force-reload

And that's all!

Yeah, for all you other newbs like me who tried to enable rewrite mod 7,000 times and even considered reinstalling flippin apache, make sure you set AllowOverride All in sites-enabled instead of messing with httpd.conf. Dang, I just wasted an hour, but on the happy side, [I learned about kill]("http://23rdworld.com/2008/01/17/kill-is-your-friend/")!

---

### Post by yasar on 2008-05-14
This worked for me.. Thanks..
> **Pekz0r said:**
> I've found out the solution!

Change AllowOverRide None in /etc/apache/sites-available/default to AllowOverRide All(or something else, but not None). Apache won't read the rewrite rules nor the .htaccess-files if AllowOverRide is set to None.

Hope that helps you too!

---

