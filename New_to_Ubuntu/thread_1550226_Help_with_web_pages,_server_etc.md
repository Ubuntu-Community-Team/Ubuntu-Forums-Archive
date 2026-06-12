---
title: "Help with web pages, server etc"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by ozstar on 2010-08-10
HI,

I have been indoctrinated by MS for 30 years and am having trouble getting me head around Linux.  Shame I didn't start here as it seem so much better, anyway back to base...

I have the latest version with all the latest updates and also have installed webmin although have hardly looked at it.

To let you know where I am at..
I use Linux on shared servers, ftp and all the rest and also use wamp on my xp box. I also have a good grip on html etc.

I want to install all the sites on I have on shared servers onto my Linux box so I can in future make changes here as a test, then upload to the servers.  This box will not be used as a server to the public, just for me to see. 

I hope someone can give me  a nudge in the right direction.

I am not sure where to load my sites. At the moment I have them in Home/david/Public. e.g   Home.david/Public/sitenumber1/

Is this the correct place for them?

In browser whe I insert localhost I get.. It works, This is th default web page etc.. but no content is added yet.

At this stage in wamp, I see links to all my sites, but here I don't. The in wamp I have a hosts file with the sies listed.

Should I have a host style file here as well. If so where would I find it?

If I do this file correctly will my sites list on this 'localhost' page?

Also, 

When I enter the url  //localhost//mysitenumber1/  I get the home page but,

when I enter //localhost/mysitenumber1/thisdir/   I get a not found altho it is there and ther is both a index.html and a index.php file there.

Why will it not see these?

Thanks,



oz

---

### Post by sandyd on 2010-08-10
> **ozstar said:**
> HI,

I have been indoctrinated by MS for 30 years and am having trouble getting me head around Linux.  Shame I didn't start here as it seem so much better, anyway back to base...

I have the latest version with all the latest updates and also have installed webmin although have hardly looked at it.

To let you know where I am at..
I use Linux on shared servers, ftp and all the rest and also use wamp on my xp box. I also have a good grip on html etc.

I want to install all the sites on I have on shared servers onto my Linux box so I can in future make changes here as a test, then upload to the servers.  This box will not be used as a server to the public, just for me to see. 

I hope someone can give me  a nudge in the right direction.

I am not sure where to load my sites. At the moment I have them in Home/david/Public. e.g   Home.david/Public/sitenumber1/

Is this the correct place for them?

In browser whe I insert localhost I get.. It works, This is th default web page etc.. but no content is added yet.

At this stage in wamp, I see links to all my sites, but here I don't. The in wamp I have a hosts file with the sies listed.

Should I have a host style file here as well. If so where would I find it?

If I do this file correctly will my sites list on this 'localhost' page?

Also, 

When I enter the url  //localhost//mysitenumber1/  I get the home page but,

when I enter //localhost/mysitenumber1/thisdir/   I get a not found altho it is there and ther is both a index.html and a index.php file there.

Why will it not see these?

Thanks,



oz
here, run this
move your files out of "Public" for the time being.
run
```

sudo mv /var/www /var/www-bkp
sudo ln -s /home/username/Public /var/www


```then, drag your files back into public (this was to prevent a typo from possibly wiping out your sites).

If your getting permission errors, try running
```

chmod -R 667 ~/Public
```

---

### Post by ozstar on 2010-08-11
Many thanks Sandy.

I did do that but nothing seemed to change so I took a search for one of the sites I had and came up with two identical versions. 

One in 
/opt/lampp/htdocs
Owner root
Group root
Couldn't share- Nautilus needs to add perms - could not change perm of folder
At the bottom of the panel it says .. you are not the owner etc

and the other in

/var/www-bkp
Owner nobody group no group
Couldn't share- Nautilus needs to add perms - could not change perm of folder
At the bottom of the panel it says .. you are not the owner etc

So it looks like they are in lampp and those in Public are not being accessed, not even by this earch I did.

I also see the Lampp Menu face which I clicked and it said it started.

I looked in /opt/lampp/ and sure enough there were all my site files however the browser with /localhost/ did not look here but in Public.

This is obviously a mess and looks like we have the unbuntu server running as well as lampp. 

Also it is obvious I am a newby so how would I get myself out of this so that I maybe only run lampp as I do use wamp on the xp box so understand the conf files a litle etc.

If the unbuntu server is just as easy then that is also fine however I need to be able to use one of them so that I can access my files.

Sorry to be a drag, but can I get some direction please feom someone.

BTW. I also have installed webmin which seems to work well.

Thanks

oz

---

### Post by sandyd on 2010-08-11
> **ozstar said:**
> Many thanks Sandy.

I did do that but nothing seemed to change so I took a search for one of the sites I had and came up with two identical versions. 

One in 
/opt/lampp/htdocs
Owner root
Group root
Couldn't share- Nautilus needs to add perms - could not change perm of folder
At the bottom of the panel it says .. you are not the owner etc

and the other in

/var/www-bkp
Owner nobody group no group
Couldn't share- Nautilus needs to add perms - could not change perm of folder
At the bottom of the panel it says .. you are not the owner etc

So it looks like they are in lampp and those in Public are not being accessed, not even by this earch I did.

I also see the Lampp Menu face which I clicked and it said it started.

I looked in /opt/lampp/ and sure enough there were all my site files however the browser with /localhost/ did not look here but in Public.

This is obviously a mess and looks like we have the unbuntu server running as well as lampp. 

Also it is obvious I am a newby so how would I get myself out of this so that I maybe only run lampp as I do use wamp on the xp box so understand the conf files a litle etc.

If the unbuntu server is just as easy then that is also fine however I need to be able to use one of them so that I can access my files.

Sorry to be a drag, but can I get some direction please feom someone.

BTW. I also have installed webmin which seems to work well.

Thanks

oz
Theres the problem.
XAMPP and LAMPP cannot be run at the same time.
Since your using webmin, run this to get rid of xampp (webmin is for LAMPP, not XAMPP)
```

sudo /opt/lampp/lampp stop
sudo mv /opt/lamp /opt/lamp-disabled
sudo /etc/init.d/apache2 restart

```

---

### Post by ozstar on 2010-08-11
Thank you again

Followed that but got this in terminal..

Restarting apache2
Warning: DocRoot [var/www/]does not exist
apache2: Uisng 127.0.0.1 as ServerName

..waiting..

Warning: DocRoot [var/www/]does not exist
apache2: Uisng 127.0.0.1 as ServerName

I tried browser.. localhost and 127.0.0.1 but got 'was not found'
Server at localhost Port 80

I saw that the lampp dir was now -disabled and that there were site index files in Home/david/Public/1300rentals/

Thanks

oz

---

### Post by sandyd on 2010-08-11
> **ozstar said:**
> Thank you again

Followed that but got this in terminal..

Restarting apache2
Warning: DocRoot [var/www/]does not exist
apache2: Uisng 127.0.0.1 as ServerName

..waiting..

Warning: DocRoot [var/www/]does not exist
apache2: Uisng 127.0.0.1 as ServerName

I tried browser.. localhost and 127.0.0.1 but got 'was not found'
Server at localhost Port 80

I saw that the lampp dir was now -disabled and that there were site index files in Home/david/Public/1300rentals/

Thanks

ozreplace  *username* with your username
```

sudo rm /var/www
sudo ln -s /home/*username*/Public /var/www
```

---

### Post by ozstar on 2010-08-11
I assume maybe incorrectly, that this is because a file is wrong.

This is default  in apache2/sites-enabled

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

-----------

apache2/httpd.conf is empty

Thanks


oz

---

### Post by ozstar on 2010-08-11
I guess disregard my last post which I did befiore I saw your last.

I did that command and yes ..Yippeee!! it gets to the site.

Many many thanks..

Now do I have to insert in any file the names of the site I will be using or will it pick them up just because they are there?  For example in xamp we had to put them in a host file.

oz

---

