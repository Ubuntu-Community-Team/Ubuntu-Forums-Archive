---
title: "Lighttpd or Apache? Which Is easier?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by nevets04 on 2009-10-21
Lighttpd or Apache? Which Is easier? Also, can you link me to a good tutorial?
Edit: I now have apache. How do I run .py scripts on it?
> 
I finally got apache installed. I moved my .cgi python web application to var/www/cgi-bin however when I went to 127.0.0.1/cgi-bin/web.cgi but it said the web address didn't exsist. So I put the file in in var/www/ and it just read what was in the script, it didnt execute it. So I tried saving it as a .py, but when I did that and went to 127.0.0.1/web.py it asked If I wanted to download web.py. Finally I tried putting the .py in var/www/cgi-bin but again, when I went to 127.0.0.1/cgi-bin/web.py, apache said that it wasn't on the server. Anyone got any ideas?
~nevts04~


---

### Post by martrn on 2009-10-21
The difference between lighttpd and apache is only that lighttpd will *not* consume as much system resources as apache will.  Apache will consume many MB of memory will running on your system, but usually no a great deal extra (difference) in terms of processor usage.

Apache is better because it is better supported and there are many more guides on how-to administer apache.

If you are doing any kind of PHP development, you will usually also be using Apache at the same time.  This is the fast way to get PHP up and running on your Ubuntu machine.

From a command shell, you will run the following commands:

```
    sudo apt-get install apache2
    sudo apt-get install php5
    sudo apt-get install libapache2-mod-php5
    sudo /etc/init.d/apache2 restart
```

Your internet browser files will now be found in /var/www/ which is just usually a couple of html documents released with the standard apache distribution.  From here it is simply a matter of following any tutorial on the internet on how to build websites.  Just put your .php scripts, .jpgegs, .pngs, and .html files in your /var/www directory.

Most of the time if you are doing any website building you will be better to learn php or html, and would be better to read a php book, there are many, apache is simply a matter of installing it and letting apache do its job.

---

### Post by nevets04 on 2009-10-21
> **martrn said:**
> The difference between lighttpd and apache is only that lighttpd will *not* consume as much system resources as apache will.  Apache will consume many MB of memory will running on your system, but usually no a great deal extra (difference) in terms of processor usage.

Apache is better because it is better supported and there are many more guides on how-to administer apache.

If you are doing any kind of PHP development, you will usually also be using Apache at the same time.  This is the fast way to get PHP up and running on your Ubuntu machine.

From a command shell, you will run the following commands:

```
    sudo apt-get install apache2
    sudo apt-get install php5
    sudo apt-get install libapache2-mod-php5
    sudo /etc/init.d/apache2 restart
```

Your internet browser files will now be found in /var/www/ which is just usually a couple of html documents released with the standard apache distribution.  From here it is simply a matter of following any tutorial on the internet on how to build websites.  Just put your .php scripts, .jpgegs, .pngs, and .html files in your /var/www directory.

Most of the time if you are doing any website building you will be better to learn php or html, and would be better to read a php book, there are many, apache is simply a matter of installing it and letting apache do its job.

Thanks, I got apache installed. However this was to develop python web applications. I moved my .cgi python web application to var/www/cgi-bin however when I went to 127.0.0.1/cgi-bin/web.cgi but it said the web address didn't exsist. So I put the file in in var/www/ and it just read what was in the script, it didnt execute it. So I tried saving it as a .py, but when I did that and went to 127.0.0.1/web.py it asked If I wanted to download web.py. Finally I tried putting the .py in var/www/cgi-bin but again, when I went to 127.0.0.1/cgi-bin/web.py, apache said that it wasn't on the server.

---

### Post by martrn on 2009-10-21
> **nevets04 said:**
> Thanks, I got apache installed. However this was to develop python web applications. I moved my .cgi python web application to var/www/cgi-bin however when I went to 127.0.0.1/cgi-bin/web.cgi but it said the web address didn't exsist. So I put the file in in var/www/ and it just read what was in the script, it didnt execute it. So I tried saving it as a .py, but when I did that and went to 127.0.0.1/web.py it asked If I wanted to download web.py. Finally I tried putting the .py in var/www/cgi-bin but again, when I went to 127.0.0.1/cgi-bin/web.py, apache said that it wasn't on the server.

See : [http://ubuntuforums.org/showthread.php?t=91101]("http://ubuntuforums.org/showthread.php?t=91101")
about installing mod python.

you need to install mod-php for running php scripts mod-python fo running .py scripts [....etc....etc....]

I don't know anything about python either in a terminal or running python scripts on a web server sorry.

---

### Post by nevets04 on 2009-10-21
Re: Python and Apache2 (mod_python)
> 
[EDIT] WelterPelter, I just saw that you said you used libapache-mod-python2.4 which means you are using apache not apache2. I wrote this for apache2, I dont know how different they are but i guess it wont work, i suggest installing apache2 and libapache2-mod-python[/EDIT]

To enable mod_python:
Code:

cd /etc/apache2/mods-enabled/
sudo ln -s ../mods-available/mod_python.load mod_python.load

To enable the parsing of .py scripts:
Code:

cd /etc/apache2/sites-available/
sudo gedit default

On line 10 you should have:
Code:

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

Change it to:
Code:

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                allow from all

                AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On

                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

Save the file.
Now restart your server:
Code:

sudo /etc/init.d/apache2 restart

Test it:
Code:

sudo gedit /var/www/test.py

insert these lines:
Code:

def index(req):
  return "Test successful";

and it should work
visit [http://localhost/test.py](http://localhost/test.py) and it should say "Test successful" in plain text

After restrting the server I get this:

```
 
* Restarting web server apache2                                                apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/mods-enabled/mod_python.load: No such file or directory

```

:(:(

---

### Post by nevets04 on 2009-10-22
bump

---

### Post by yeats on 2009-10-22
Looking at this...

> * Restarting web server apache2                                                apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/mods-enabled/mod_python.load: No such file or directory

Look at line 185 of /etc/apache2/apache2.conf.  Does it actually say "mod_python.load"?  After installing the libapache2-mod-python package, I see /etc/apache2/mods-enabled/**python**.load ...

---

