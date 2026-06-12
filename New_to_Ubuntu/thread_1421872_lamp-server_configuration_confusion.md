---
title: "lamp-server: configuration confusion"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by crantok on 2010-03-04
I installed lamp-server on Xubuntu 9.04 using tasksel. So far so good. Then the following chain of things happened that has left me really confused about Apache's configuration. I'd like to point out that I was paranoidly restarting Apache and clearing my browser's cache between all the steps:

A) Navigating to [http://localhost](http://localhost) showed the default Apache index.html; "It works!"

B) Replacing index.html with an index.php that just contained ```
<?php phpinfo(); ?>
``` and navigating back to [http://localhost](http://localhost) gave me a dialog box saying: ```
You have chosen to open
``` but with no file name displayed, just whitespace.

C) I found some advice on the net and added ```
DirectoryIndex index.html index.php
``` to /etc/apache2/httpd.conf, which stopped the behaviour in step (B) but now did not seem to process or display anything in PHP tags. (Text outside of PHP tags was displayed.)

D) Further searching prompted me to add ```
AddType application/x-httpd-php .php
``` to httpd.conf and that solved the problem: e.g. now I could see the output from phpinfo().

E) I commented out all the lines in httpd.conf (restarted apache, cleared browser cache) and everything still works. PHP code in index.php is still being processed.

I have 3 questions:

1) Should I have posted this somewhere other than absolute beginner talk? I'm not confident about what constitutes a non-beginner question.

2) Should I have needed to alter any configuration files or should lamp-server have worked "out of the box"? I've found conflicting information about this.

3) Does Apache persist configuration information in some way so that my configuration file edits have an effect across restarts?

---

### Post by J V on 2010-03-04
1: Yes, there is a programming forum somewhere, but it will take a few clicks to get there...
2: Out of the box
3: Not that I know of...

Take a course in php ;)
```
<?php echo phpinfo(); ?>
```

---

### Post by sandyd on 2010-03-04
install php5.
apache does not include that by default.

---

### Post by crantok on 2010-03-05
@ J V: I'm not an absolute beginner in PHP, just in setting up a web-server.

@carlee: I didn't install apache directly, I used tasksel to install lamp-server. PHP (or at least the apache PHP module) was installed in that process.

---

### Post by crantok on 2010-03-05
Okay. Now this seems really weird to me but maybe it makes sense to someone else:

I have my own index.php and Apache's index.html in /var/www. If I navigate to [http://localhost](http://localhost) then index.html is displayed. This makes sense to me.

If I move index.html out of /var/www, then index.php gets displayed instead. This too makes sense to me.

If I leave the original Apache index.html in the /var/www/ directory **but** I rename it to index.html.bak then when I navigate to [http://localhost](http://localhost) I get the "You have chosen to open     " dialog box. I don't understand this.

Is there some property of Apache's default index.html file that causes apache to serve it to my browser even when it is renamed and another valid file (i.e. index.php) is present?

---

### Post by J V on 2010-03-05
Not that I know of...

Are you echoing the phpinfo? If not it will just try to send you the file by itsself...

---

### Post by crantok on 2010-03-05
I don't have any problem with index.php being displayed. When it's served, it gets displayed correctly. (And no, it does not include echo. It doesn't seem to need it.)

The thing that's puzzling me is the circumstances under which it does **not** get served.

---

### Post by J V on 2010-03-05
Is there a .htaccess file there? If not, post your sites-enabled/default file...

---

### Post by crantok on 2010-03-05
There's no .htaccess file in the /var/www directory. Please let me know if there's anywhere else I should look for it.

Here is the text of the only file in /etc/apache2/sites-enabled/. It is called 000-default

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

---

### Post by crantok on 2010-03-05
Well, it was easy to confirm that it was not a property of Apache's default index.html by executing
[INDENT]sudo touch index.html.bak
[/INDENT]The file created this way had the same effect. I also tried 
[INDENT] sudo touch index.bak
sudo touch index.php.bak
sudo touch index.htm.bak
sudo touch index.html.gobbledigook
[/INDENT] but none of them triggered the same behaviour, so I guess index.html.bak is just some kind of meaningful name to Apache. A google search for[INDENT]apache "index.html.bak"
[/INDENT]turned up a few thousand results including[INDENT][http://ubuntuforums.org/showpost.php?p=7934615&postcount=8](http://ubuntuforums.org/showpost.php?p=7934615&postcount=8)
[/INDENT]

---

### Post by J V on 2010-03-05
Wow, never knew .bak was a real extension :P

---

