---
title: "Apache2 , access from the www"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by stevoo on 2008-08-29
I am trying to bring the small test site that i created onto the web, using apache2. 

I created a new site in sites-available named it my site 
and gave it the following 
```
<VirtualHost 139.222.232.252>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

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
```

 i then changed it to use that one by :  sudo a2ensite mysite
did a graceful restart ... and after a lot of trial and error i cannot push the site to go live. 

Any tips please ? 
i tried apache site for help, still i couldnt make it go up

:popcorn:

---

### Post by mrsteveman1 on 2008-08-29
So is apache running? is it listening on port 80? can you get to at least some default "nothing here' page by pointing a local browser at 127.0.0.1:80 ?

---

### Post by stevoo on 2008-08-30
i can view my website normally if i go to localhost, 127.0.0.1 and 139.222.232.252

But i cannot make the site live. 

Is there something else that needs to be done ?

---

### Post by scragar on 2008-08-30
have you tried removing the bold line(s)?
```

    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
[B]        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
[/B]    </Directory>

```

---

### Post by stevoo on 2008-08-30
Tried that but nothing.
[139.222.232.252]("139.222.232.252")
is still unacessible.....

---

### Post by az on 2008-08-30
Does your ISP block port 80?  Many of them do.

---

### Post by stevoo on 2008-08-30
i wouldnt be sure :)

But it could be the university firewall and stuff. . . 

Offcourse i have no way of knowing .... 

But the setting should be ok and working ?

---

### Post by mrsteveman1 on 2008-08-30
The settings look fine.

If you want to test things, change the Listen line to 81 or something similar and restart apache, then see if it works.

---

