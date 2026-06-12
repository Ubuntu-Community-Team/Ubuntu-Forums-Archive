---
title: "Apache 403 Forbidden on localhost directory change"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by viva_cthulhu on 2007-05-19
Greetings, and thanks in advance. Also, apologies if I am posting in the wrong forum - it was this or General Help, I went for the most specific one...
I installed Apache, mysql and php5 for offline website testing, and changed the base website folder to one on my fat32 partition; now I'm getting a 403 Forbidden when I try to access localhost.
I saw this on help forums and tried it - to no avail
```
sudo chmod 777 -R *.* /media/c/Documenti/Site/
```
Also tried a lot of different chmod syntaxes beside this (r+o, just the directory without the finale slash...)
Eerily, even if I access the browser as root it still gives me a 403.
Apache seems to be ok in itself, works fine in its /var/www.
Posting my /sites-enabled/default-000
NameVirtualHost *
```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /media/c/Documenti/Site/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/c/Documenti/Site/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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
/sites-available/default points to the same directories, and I tried this syntax with both a final slash after the directory and without.
Again, thanks in advance!

---

### Post by tturrisi on 2007-05-19
Is this: /media/c/Documenti/Site/ mounted?
You can edit /etc/fstab to have that mounted at boot:
Assumed that /dev/hda1 is the location of Windows partition (FAT)
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

    * Append the following line at the end of file 

/dev/hda1    /media/c/Documenti/Site vfat  iocharset=utf8,umask=000  0    0

reload fstab:
sudo mount -a

---

### Post by viva_cthulhu on 2007-05-19
It's mounted alreadly - the whoole windows partition c drive is mounted as /media/c. 
Could there be some sort of uber-permission relative to fat32 partitions? So, maybe I chmodded the directory as accessibile but the drive still rings as non accessibile to apache... No, that makes no sense.
Could it be some conflicting application? Can't think of anything that could... the most server-like thing I have running is krusader...
Thanks!

---

### Post by viva_cthulhu on 2007-05-22
Greetings again... I still couldn't manage to solve that problem.
While apologizing for my incompetence (quite surely it must be something rather obvious) I would still kindly ask for help.
I did not add on my last post that the problem concerns the cross-platform usage of the site directory - therefore, providing means to access a file on a linux partition from xp would solve the problem as well.
Once again, thanks in advance!

---

### Post by tturrisi on 2007-05-22
The fat32 partition is owned by root.
Why not just use the default apache dir /var/www for the sites?  It will be accessable by any computer.

---

### Post by viva_cthulhu on 2007-05-22
Thanks again Turrisi!
I would use the default directory - since it works - but it wouldn't be accessibile on the machine, should it be booted in windows (it's a dual boot - shameful but I can't give up on videogames) since, as far as I know, an ext3 partition should be unaccessibile by xp - especially in r+w mode!
I used chmod 777 on the partition, but it doesn't seem to help. Besides, if I try to access localhost as root (e.g. sudo firefox) I still get a 403 - shouldn't happen if it was a simple permission problem... I guess. Unless I have to be, like, *uber* root or something...
Is there a way to have r+w access on a linux partition from windows?
Again, thanks!

---

### Post by tturrisi on 2007-05-22
Just host the pages in the www dir and keep a copy on the fat32 partition.  Edit using the fat32 files and upliad them or copy them to www.  Myself, I use a separate older comp just for web dev, to host the pages.  I develop on other comps and can upload from any of them.

---

### Post by viva_cthulhu on 2007-05-23
...I never looked at it like that. Yeah, it's a bearable sacrifice!
Thanks for all your patience. I'll do that!

---

### Post by jhoseini on 2008-05-25
so, really there is no way to use htdocs in fat32? :(
i have win and lnx both, and i need to use common wwwroot in my localhost
i want to use /media/PROG/Xampp/htdocs as wwwroot for windows and linux
but it returns 403 forbidden :(
thanks

---

