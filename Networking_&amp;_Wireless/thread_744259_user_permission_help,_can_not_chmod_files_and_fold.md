---
title: "user permission help, can not chmod files and folder"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by Oldsoldier2003 on 2008-04-04
> **Auston said:**
> Hi everybody

I have my own Linux server, I just creat a account via WHM

/home/johnterry

I moved all my files and folders from /usr/local/apache/htdocs/* to my new account place : /home/johnterry/public_html

and I login to new account with ftp program but I can not chmod files and folders with this account, I dont know why ? I must set permission for user "johnterry" ? or I miss something ?

I am new with Linux server, please help me

Thanks for your time !

here is a sample:
chuck@ubuntu:~$ cat /etc/apache2/sites-available/default
```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot/home/johnterry/public_html/
	<Directory />
		Options FollowSymLinks
		#AllowOverride None
		AllowOverride All
	</Directory>
	<Directory /home/johnterry/public_html/logs/>
		Options Indexes
		AllowOverride All
		Order allow,deny
		allow from all
		
	</Directory>
	<Directory /home/johnterry/public_html/images/>
		AllowOverride all
		Order allow,deny
		allow from all

	</Directory>
        <Directory/home/johnterry/public_html/includes/>
                AllowOverride all
                Order allow,deny
                allow from all

        </Directory>

	

	ScriptAlias /cgi-bin/ /home/johnterry//public_html/cgi-bin/
	<Directory /home/johnterry/public_html/cgi-bin">
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

```
sudo chown -R johnterry:johnterry /home/johnterry/pulic_html
```

---

