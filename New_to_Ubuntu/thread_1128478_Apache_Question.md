---
title: "Apache Question"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by joec369 on 2009-04-17
Hello I'm trying to setup Apache Web Server.  What I have done:

Installed Apache
Turned it on
Made a config file
Made a directory where the website is /home/(username)/public_html
Made a simple webpage

It works if I'm on the Ubuntu Machine.  I type in [http://localhost/](http://localhost/) in FF and it comes up with my simple html site I made.  

But if I try to access the website from another computer on my LAN it doesn't work.  I'm typing in [http://10.0.2.15/](http://10.0.2.15/) (10.0.2.15 is the IP address of Ubuntu Machine) in FF.

Both machines can ping each other.  Also should mention that both machines are Virtual box guests.  Both in the Same network/subnet.

Any Help would be greatly appreciated.

---

### Post by Funkydonut5000 on 2009-04-17
Try having a friend access your web page.  I think I remember reading something about problems viewing pages from inside your network (through web browser).

---

### Post by ASchweitzer on 2009-04-17
If you have a firewall running, make sure you open port 80 for incoming traffic.

Also check your config to make sure you're running Apache to listen on port 80. Although if [http://localhost](http://localhost) works, this shouldn't the a problem.

---

### Post by ostrm on 2009-04-17
> **Funkydonut5000 said:**
> Try having a friend access your web page.  I think I remember reading something about problems viewing pages from inside your network (through web browser).

That doesn't make much sense to me. In the end it's just a http request to some ip ...

Make sure your firewall doesn't block access to port 80.

EDIT: oh, too slow ... :-)

---

### Post by joec369 on 2009-04-17
I'm not too sure how to use FireWalls on Ubuntu.  I downloaded FireStarter and put an incomming exception in for the IP address I was using to try to access the Website.  It didn't work.  I tried disabling the fire wall all together.  That' also didn't work.

Is there any default program that comes installed already in ubuntu that I can use to configure the firewall?

Any other ideas?

---

### Post by joec369 on 2009-04-17
I also just tried adding an inbound exception for HTTP Port:80 for Everyone.  That also didn't work.

---

### Post by joec369 on 2009-04-17
Here is the config I am using.  Let me know if you see any problems:


<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/joe369/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/joe369/public_html>
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

---

### Post by joec369 on 2009-04-17
Anyone have any suggestions

---

### Post by ASchweitzer on 2009-04-20
> **joec369 said:**
> Here is the config I am using.  Let me know if you see any problems:


<VirtualHost *:80>


I've compared this to my own conf, and the only differences I can see is the above :80, which is not present in my config, and the location of your directory. I'm using the default, /var/www though I can't see that being an issue (other than file permissions, maybe? but that would be dependent on the apache process, not the html request).

I would try to remove :80 from that VirtualHost arguement, and make sure your ports.conf is set to listen on port 80.


Also, are you sure you're entering the LAN IP? 10.X.X.X looks like an external IP to me. If it is, try it on port 10000 or something, and forward that port (in your router) to port 80 for the Ubuntu machine.


--EDIT:

The reason I say port 10000 above, is that most ISPs will not allow incoming port 80 traffic, but you'd have to check with yours.

Also, firewall programs are all really just a frontend for editing iptables. I recommend ufw or gufw (the GUI of ufw), as firestarter is no longer supported.

---

