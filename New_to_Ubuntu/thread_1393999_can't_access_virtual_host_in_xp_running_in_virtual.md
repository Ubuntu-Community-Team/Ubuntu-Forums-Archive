---
title: "can't access virtual host in xp running in virtual box"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by mvalviar on 2010-01-30
I have ```
test 10.0.2.2
``` on the windows hosts file. And this is what I have under /etc/apache2/test.conf ```
<VirtualHost test:80>
	ServerAdmin webmaster@localhost
        NameVirtualHost test

	DocumentRoot /var/www/test
	<Directory />
		Options FollowSymLinks
		AllowOverride All
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
in ubuntu I can access whatever is in /var/www/test by pointing my browser to [http://test](http://test) (I have 127.0.0.1 test in my /etc/hosts file)

But in my virtual xp I get the contents of /var/www which is the docroot of /etc/apache2/sites-available/default.

---

### Post by mvalviar on 2010-01-30
up

---

### Post by ymra on 2010-01-30
try changing the network adapter in virtual box's networking settings.

---

### Post by jobsworth on 2010-01-30
This is the kind of thing I do all of the time.
If I understand you correctly you are running
Ubuntu with an Apache web server
and a Sun virtual box in which you have installed Windows XP.

You don't mention the hosts file.
It is really important else how can your Windows XP
find anything on your system or intranet.
You don't have a domain name server like BIND
you rely on your HOSTS file.

I suggest that you need to define a fixed TCP/IP
for your intranet web site and internet connection like 192.168.1.45.
Do this in Ubuntu. It is a bit buggy.
The numbers are difficult to enter.
Right click and then edit connections - manual
everything is 192.168.1.1 and the mask is 255.255.255.0.

Good to give your web site a name like test.com
Add ServerName test.com instead of NameVirtualHost test.
Instead of test:80 have *:80

Call your web page index.html
and put it in /var/www/
replace /var/www/test by /var/www in your
etc/apache2/sites-enabled/000-default file
or whatever else you decide to call it.


Then in Windows XP add a line in your HOSTS file
which lives in c:\windows\system32\drivers\etc\
192.168.1.45 test.com

Now typing test.com
in a browser firefox or IE8 in Windows XP
should action your index.html

Should work.
It is easier to do than to explain.

---

