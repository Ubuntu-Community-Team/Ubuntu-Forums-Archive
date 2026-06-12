---
title: "Mod_rewrite &amp; .htaccess"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by eDRoaCH on 2008-04-11
Trying to get Mod_rewrite working on my dev system. I am new to this so I am not sure where my problem is, but by reading various posts all over the forums and thru google I see many others have problems with this. It could be my regex itself as I am brand new to it. 

 I am trying to turn [http://localhost/?page=articles](http://localhost/?page=articles) into [http://localhost/articles/](http://localhost/articles/)

The most useful post I found seems to be: [http://ubuntuforums.org/showthread.php?t=255556&highlight=mod_rewrite&page=2](http://ubuntuforums.org/showthread.php?t=255556&highlight=mod_rewrite&page=2)

but still I have no luck. I am new to .htaccess, regex and mod_rewrite so I am really not sure where my problem is. 

from /etc/apache2/sites-enabled/000-default, where I changed from AllowOverride None to All: 
```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>
```

from apache2ctl -l:
```
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

```

I also get this:
```
 sudo a2enmod rewrite
This module is already enabled!
```



I have messed with my .htaccess file so much I am completely lost now, but this is what it looks like for the moment:
```
Options +FollowSymLinks
RewriteEngine on
RewriteRule ^\?page=([.*]+)$ /$1
```

Can someone tell me where I am going wrong here and maybe a way to do a basic test of mod_rewrite or at least enable and find a log file somewhere? My httpd.conf is completely blank so I am guessing Ubuntu isn't using it.

For reference, I've got 7.10 fully updated (as of yesterday when it downloaded a few non-web related updates)

As I said, I am brand new to this and I really have been surfing all over creation for input. If you need any further info please let me know.

---

