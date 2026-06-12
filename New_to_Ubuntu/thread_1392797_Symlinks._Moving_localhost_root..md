---
title: "Symlinks. Moving localhost root."
date: 2010-01-28
forum: New to Ubuntu
---

### Post by colinmccubbin on 2010-01-28
I'm new to Linux and have just set up a dualboot system on a new pc, winxp and ubuntu 9.10.. 

I need to use some of my win specific software such as dreamweaver to create php and html pages so set up a third partition as ntfs where I could share sites. 

Because I really wanted to spend as much time in Ubuntu as possible (and try out other linux based code editors, the Gimp too etc)I set up apache and php in Ubuntu rather than windows by doing "Synaptic > Edit > Mark Packages by task. Select LAMP server and clicking OK."

Opened firefox, entered [http://localhost](http://localhost) and got the "it works!" page... I eventually found that the default installation's server root is in var/www/  

Now, I want to set/change the default to be my third partition so I can save pages there from windows and Ubuntu and serve them.

In the ntfs partition I have created a folder called htdocs, from which I'd like apache and localhost to serve pages. I then right clicked it, selected "Make link", and then copied the resulting "Link to htdocs" and dropped it into var/www/ 

I placed a file, test.php containing <?php phpinfo();?>  in htdocs, and tried [http://localhost/test.php](http://localhost/test.php)  but just get a 404 not found.

Obviously my limited understanding of symlinks is faulty, I'd expected that files in htdocs would now be treated as though they were in var/www/, but after scratching my head and googling etc I am no nearer working out how to do this, or what I am doing wrong. 

Any help would be very gratefully received!

---

### Post by J V on 2010-01-28
[http://localhost/Link to htdocs/test.php]("http://localhost/Link%20to%20htdocs/test.php")

Move it up a directory and rename it www, overwrite the www folder...

---

### Post by colinmccubbin on 2010-01-28
> **J V said:**
> [http://localhost/Link to htdocs/test.php]("http://localhost/Link%20to%20htdocs/test.php")

Move it up a directory and rename it www, overwrite the www folder...

Thanks, but by 'it' you mean what?

By the way, I tried your example of [http://localhost/Link to htdocs/test.php]("http://localhost/Link%20to%20htdocs/test.php") and get a 403 Forbidden message... ..

Colin

---

### Post by J V on 2010-01-28
by it I meant the symlink...

when the server looks at /var/www it doesn't see an index, it sees a symlink, so if you go to localhost/link it will go into the link...

the 403 error means it found the file (through the symlink) but the server doesn't have access to the other HD (pesky permissions and all that) the easiest way is to make a folder in your home and edit the config files to look for the site there instead...

[http://ubuntuforums.org/showthread.php?t=1132401](http://ubuntuforums.org/showthread.php?t=1132401)

---

### Post by bodhi.zazen on 2010-01-28
You would need to configure Apache to follow links, and that is not considered to be good forum as it is a potential security issue.

IMO, Better to define the root as /wherever/you/want rather then /var/www

This page is often helpful:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by colinmccubbin on 2010-01-28
> **J V said:**
> The easiest way is to make a folder in your home and
edit the config files to look for the site there instead...


I presume that you mean my home directory when in Linux? Unfortunately then I wouldn't be able to write to that from windows... I had read that I could do this by installing Ext2 IFS, but under 9.10  Ext2_IFS doesn't work(!) since the file system it creates is  Ext4, which Ext2_IFS doesn't understand.



> **bodhi.zazen said:**
> You would need to configure Apache to follow links, and that is not
considered to be good forum as it is a potential security issue.

IMO, Better to define the root as /wherever/you/want rather then
/var/www

Please excuse me, (I'm a beginner  ;-)  I can see that I can I can use the apache config file(s) to point at a new path, but I'm not sure what the path to my shared ntfs partition actually is. Sounds stupid I know, but although I know that to Ubuntu all files, folders, hardware devices etc are just nodes on the directory tree, starting from / which is the absolute root, I don't see how extra drives fit into that scheme and how
they are addressed.

Looking at my computer in the media File Browser I see my ntfs partition named as 221 GB Filesystem, but if I right click that and select properties I see name: 12830E7515E3BC8E and location as /media

So, is the path I need to put in the apache config for me to get apache to start in the htdocs folder thus /media/12830E7515E3BC8E/htdocs ?

I've found httpd.conf in /etc/apache2/ but unfortunately it is empty...??

But I've also found /etc/apache2/sites-available/default which does contain these lines: 

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
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

I'm quite happy to keep on muddling along, (have I found the right config file?) but again some advice as to which lines to change and the significance of the 

```
Alias /doc/ "/usr/share/doc/"
``` section would be appreciated.

Thanks!

---

### Post by Miljet on 2010-01-28
I don't know anything about apache but perhaps the following will clarify a few things for you. Linux can, and does, use uuid (which is what the long number sounds like) and names (such as 221 gb filesystem) interchangeably. In other words you can use one or the other in most instances. In either case, the partition is mounted at /media. So you can access the partition just by entering /media. Thus from your example, it should be /media/htdocs.

Hope this didn't just confuse you more. You might want to take a look at your /etc/fstab file.
```
cat /etc/fstab
```

---

### Post by louieb on 2010-01-28
Like you I kind of muddled around  - anyway look for the line that starts with  **document root **in **sites-enabled and sites-available**  - all I did was change /var/www to the path to the folder I  my html and index files in.  

Once you figure out what the path is to your html documents is -

---

### Post by AndyDeGroo on 2010-03-26
Just placing symlinks in /var/www or configuring Apache's document root to /media/something is not enough unless that partition is configured in /etc/fstab to be mounted on boot.
Apache may even refuse to start if it can't read configured document root or return 404 - Not found when accessed from browser. If this is the case and you have no clue what's going on, best bet is to look inside /var/log/apache2/error.log

Possible solution:
Add that partition to fstab and set Apache's document root to directory on that partition.
If file system is NTFS and it is mounted on boot with default permissions, files will be readable and writable by anyone, but directories just by user who mounted it - root. That may be fixed by setting relevant options in fstab.

To test this I created directory /media/Win_C and added following line to my fstab: ```
UUID=2668F9BB68F989B7    /media/Win_C    ntfs user,rw,nosuid,nodev,uid=33    0    0
```
note: uid of www-data by default  is 33 (I have seen 80 on BSD)

Another solution to make partition readable by both OSs is to use ext2  or FAT.
In first case there will be no editable file permissions in windows (with Ext2_IFS), but in second - FAT does not have any permission implemented on file system level.

If this setup is for development only, permissions will not be a big problem, but if Apache hosts code for production or any code on it has to deal with file permissions, then better decide which one OS to use. I'd stick with Ubuntu.

Hope this will help.

---

