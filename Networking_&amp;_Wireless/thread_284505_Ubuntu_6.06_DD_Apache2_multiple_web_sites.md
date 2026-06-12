---
title: "Ubuntu 6.06 DD Apache2 multiple web sites"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by SteffJay on 2006-10-25
Ok....  after hours and hours of searching the FAQ's, sending post's and following Debian, Apache and Ubuntu "howto's", 5 reinstalls and hair loss, i am asking (if not pleading) for someone to give a tutorial on how to create a web server with two or more web sites using the same ip address, EG: 192.xxx.xxx.xxx THAT WORKS !!!. Some of the information given on the above tells me to edit the **httpd.conf** when apparently, that has nothing to do with 6.06 !! Others tell me to edit the **/etc/host** file, when i do, it crashes.... I now realise that there are subtle differences in the different distro's but i never realised to what a greater extent that they do. :(  What i (and probably a lot of other people) want to know is, what extra programs to install, what to add to what and how, what not to change etc..... Even pictures of the changes, that would help. I know most of you will be falling off of your chairs right now but i can assure you, this has driven me to distraction (let alone the wife giving me GBH of the ear)..... So.... Any good hearted people out there willing to take up the challenge ?? I would appreciate it greatly....  ;)  Thank's in advance !!

---

### Post by SteffJay on 2006-10-26
Ok......  Now i am going to answer my own question here. ;)  First of all, this is pertaining to Ubuntu 6.06 DD and no other distro. I say this, although it might work on 5.10 etc. This article has pictures (for my relevance if i need to do a new install) and anybody else that may benifit from it. I will assume that you have installed Apache2, PHP5 and any other programs that are needed before you follow this tutorial. Now, the first thing to do is, create as many folders you require to serve as different web sites in **/var/www/** (in this case **web1**, **web2** and **web3**). Next, make a copy of the "**default**" document in **/etc/apache2/sites-available** folder and rename it to one of the folders you created in **/var/www** (we will call it **web1** for this tutorial). Also, any other web site folders you want to serve will be here as well, **web2**.... etc. Once you have renamed it to **web1**, open a terminal and enter **sudo gedit /etc/apache2/sites-available/web1**. The only changes you need to make will look like this: 

[b]#NameVirtualHost *        [COLOR="Red"]<-----  you can edit this line out or delete it alltogether[/COLOR]
<VirtualHost *>
ServerName web1.com    [COLOR="Red"]<--------------  Add this line with the new full web site address[/COLOR]
	ServerAdmin [email]webmaster@web1.com[/email]   [COLOR="Red"]<--------- add the email address for this web site[/COLOR]
	
	DocumentRoot /var/www/web1       [COLOR="Red"]<-------------------   No trailing slash[/COLOR]
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/web1/>            [COLOR="Red"]<------------   With trailing slash[/COLOR]
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
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

</VirtualHost>[/b]

After you have amended the above, you save it and duplicate it (with the appropriate changes of course) to the other web sites you have and name it accordingly (**web2, web3 etc**). The next thing to do is to make a **link** to these three files and copy them to the **/etc/apache2/sites-enabled** folder. So, now we have (say) three folders in **/var/www/web1, web2, & web3** and the corresponding sites available in the **/etc/apache2/sites-available folder** and the three links in the **/etc/apache2/sites-enabled** folder. There is not much else to do now apart from adding the web sites to the networking section. This will allow Apache to point all of the web sites to one IP address (**192.168.x.x**). Click the **System/Administration/Networking tab**. Here are the additions that are needed to be changed:

[IMG]http://www.steffsoft.com/pics/net-set1.jpg[/IMG] [IMG]http://www.steffsoft.com/pics/net-set2.jpg[/IMG] [IMG]http://www.steffsoft.com/pics/net-set3.jpg[/IMG] [IMG]http://www.steffsoft.com/pics/net-set4.jpg[/IMG] [IMG]http://www.steffsoft.com/pics/net-set5.jpg[/IMG]

That is about it apart from restarting Apache: **/etc/init.d/apache2 restart**. I hope this tutorial will be of help to others out there and anyone that would like to contribute to this thread are more than welcome to. ;)

---

### Post by Rayzrshrp on 2007-04-23
Nice post SteffJay! Exactly what I was looking for and worked like charm.

---

### Post by SteffJay on 2007-04-23
Your more than welcome Rayzrshrp. I'm glad it has helped someone out.....  :)

---

### Post by Rayzrshrp on 2007-04-23
Although I have a second question now:

[www.thunderpunch.net](www.thunderpunch.net) loads the virtual host
but thunderpunch.net lists the default which works but also [http://thunderpunch.net/www.thunderpunch.net/](http://thunderpunch.net/www.thunderpunch.net/)

any idea where this url douobling is coming from?

---

### Post by SteffJay on 2007-04-23
No such file or directory in /etc/wordpress/wp-config.php on line 6 ?????

---

### Post by Rayzrshrp on 2007-04-26
Yeah I messed around with this a lot the other day and it seems the Wordpress install that Ubuntu installs via apt-get uses the url name to find the correct config file in /etc/wordpress

I came up with a workaround of just making a [www.thnuderpunch.net-wp-config.php](www.thnuderpunch.net-wp-config.php) and a thunderpunch.net-wp-config.php but it seems like there should be a cleaner why to fix this. How the virtual hosts are setup right now [www.thunderpunch.net](www.thunderpunch.net) takes me to my site and if i enable indexes on the defaut virtual host it goes to /var/www and lists the apache-default directory. I turned off indexes right now so people can't view my root but why is it so hard to make thunderpunch.net and [www.thunderpunch.net](www.thunderpunch.net) go to the same place without messing up my ability to host multiple vhosts?

---

### Post by hongleong on 2007-05-10
Thanks SteffJay for sharing the setup. It works for me at first try and save me much time. Kudos! :)

---

### Post by SteffJay on 2007-05-11
Your more than welcome **hongleong** :)

---

