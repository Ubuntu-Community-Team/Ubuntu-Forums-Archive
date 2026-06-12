---
title: "Apache2 Help"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by joec369 on 2009-04-20
I'm trying to setup apache2 webserver.  But I keep getting the default "It Works!" Page.  This is what I did so far:

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/(username)

sudo vi /etc/apache2sites-available/(username)

Edit Line: DocumentRoot /home/(username)/public_html/
Edit Line: <Directory /home/(username)/public_html/>

sudo a2dissite default
sudo a2ensite (username)

sudo /etc/init.d/apache2 restart

**[SIZE="5"][SIZE="3"]Am I missing something?[/SIZE][/SIZE]**

Here is Virtual host config file:

NameVirtualHost *
<VirtualHost *>
	ServerAdmin [email]joec369@hotmail.com[/email]
	
	DocumentRoot /home/administrator/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/administrator/public_html/>
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

Any Help would be greatly appreciated.

---

### Post by bladeswords on 2009-04-20
Is the problem possiably that apache has no access to the user directory?  Since apache runs as a limited user, it shouldn't have access to your user accounts home directory.

That is my guess anyway...

---

### Post by joec369 on 2009-04-20
I have set it up exactly like this before.  But for some reason this time it is not working.

---

### Post by bladeswords on 2009-04-20
Is there a file called the username in this directory?

/etc/apache2/sites-enabled

---

### Post by orlox on 2009-04-20
If you are in kind of a hurry you could go to /var/www and edit the files there directly...Not a pretty nor secure solution, but its a direct one...

---

### Post by mathman54 on 2009-04-20
Try this: 
cd to /var/www
do ls -la your should see index.html
do a sudo nano index.html
to test insert  a simple yes next to It Works! 
Open browser and go to your web site address 
click reload and you should see "It Works! Yes

---

