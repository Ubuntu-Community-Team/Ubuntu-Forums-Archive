---
title: "set /var/www/ as apache directory"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by keenlearner on 2008-05-17
Hello, after I upgrade to Hardy Heron, my apache2 directory has changed to /usr/share/apache2/default-site . When I go to [http://localhost/](http://localhost/) , it gives the "It works!" page. Now I want to set it to /var/www/ 
This is my /etc/apache2/sites-enabled/000-default file

> 
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName localhost
	Alias / /var/www/
	DocumentRoot /var/www/


	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

#	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
#	<Directory "/usr/lib/cgi-bin">
#		AllowOverride None
#		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
#		Order allow,deny
#		Allow from all
#	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


Is my setting correct ? Thanks.

---

