---
title: "RewriteRule - friendly urls  VirtualHost file"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by 007casper on 2010-08-07
Originally I had a RewriteRule that I copied from the 'default' sites-available under Apache.

It was.
> 
        <Directory /srv/www/domain.com/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
		allow from all
        </Directory>

		
I was required to change it to in order for the urls to be search engine friendly...
> 
		<Directory /srv/www/domain.com/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                </Directory>
		
I am trying to understand the difference between these two RewriteRules, and why second one allows .htaccess to be read and the other doesnt.  I do understand the second one says AllowOverride All.  But is there a specific way to say that in the first one that keeps everything same, and gives an exception to .htaccess

I am trying to break it down
first line states go to spefic 'directory', 
and I am not sure about Options Indexes FollowSymLinks MutiViews,  
AllowOverride is to None or to All (disallow and allow)
Order allow, deny ?
allow from all ?


thank you.

---

### Post by Bachstelze on 2010-08-07
I see no RewriteRule there. O.o

---

### Post by 007casper on 2010-08-08
lol.  That made laugh.  You are right.  I was thinking and writing something else, and getting ahead of myself.

I took this... 
> 
<Directory /srv/www/domain.com/public_html>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory> 

from default sites-available under Apache.  

When I had that in there, .htaccess rewrite rule didnt work for the website.  I wouldnt get clean urls.  Then, I changed it to the bottom one, and now it works.  I am trying to figure out/learn the difference between these two in the virtualhost file.  I would think the top one would've worked, but that wasnt the case...

---

### Post by Bachstelze on 2010-08-08
The difference is the AllowOverride.  It defines which directives you are permitted to set in your .htaccess.  The first one says None, meaning that your .htaccess will just be ignored.  The second one says All, mraning that everything your .htaccess contains will have effect.

---

### Post by AnimalMagic on 2010-08-08
Go to the horse's mouth :p

[http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride]("http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride")

---

### Post by 007casper on 2010-08-08
thank you both :-)

---

