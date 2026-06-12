---
title: "apache2"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by spillage2 on 2011-03-25
Hi All,

Been looking at virtual hosting using apache but would rather start from scratch. 

What would be the best way to completely remove apahce2 and all its files from my system (10.04).

Cheers Spill.

---

### Post by ~Plue on 2011-03-25
try purging all those which were installed
```
sudo apt-get purge apache2 apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common
```

---

### Post by spillage2 on 2011-03-25
Thats great thanks for the info..

I have been following [http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)


/etc/apache2/sites-available/my.conf is

<VirtualHost www.my.ath.cx:80>
ServerAdmin mail@localhost
ServerAlias [www.my.ath.cx](www.my.ath.cx)
DocumentRoot  /home/me/www/my/my.html
</VirtualHost>

Running the .html file in /home/me/www/my/my.html as file/// directly works in browser.

But using [www.my.ath.cx](www.my.ath.cx) is just linking to the it "works page"...I know I'm doing something really stupid but can see where..

Any pointer would be a great help.

---

### Post by ~Plue on 2011-03-25
'DocumentRoot' should point to  a directory, not a file..

and also, remember to restart apache after the change

---

### Post by spillage2 on 2011-03-25
Hi ~Plue,

Ok removed the .html file so its just /home/me/www/my/ and also ran sudo /etc/init.d/apache2 reload.

Still sending [www.my.ath.cx](www.my.ath.cx) to the it works page and not the .html file in ./my

Spill.

---

### Post by tordeu on 2011-03-25
> **spillage2 said:**
> Hi ~Plue,

Ok removed the .html file so its just /home/me/www/my/ and also ran sudo /etc/init.d/apache2 **[COLOR=Red]reload[/COLOR]**.


Hi, did you have a type there of did you really run "reload"? Because, you need to run:

```

sudo /etc/init.d/apache2 **[COLOR=Red]restart[/COLOR]**

```

instead of "reload".

---

### Post by ~Plue on 2011-03-25
i'm not an expert on these things either..try adding to the top of the file [FONT=monospace]
[/FONT]```
*NameVirtualHost [www.my.ath.cx:80]("http://www.my.ath.cx:80")*
```
or match the *NameVirtualHost *in /etc/apache2/sites-available/default with your virtualhost
then restart/reload again

---

### Post by spillage2 on 2011-03-25
sorry yes was a typo...


Have removed and install again following a diff guide and seem to be getting there. Just running the one site and will now add another to see how it goes.

Thanks for all the help.

Just in case anyone has the same probs the guide is here  [http://www.nitesh.com.np/website-maintenance/configuring-virtualhost-and-host-alias/](http://www.nitesh.com.np/website-maintenance/configuring-virtualhost-and-host-alias/)

Spill.

---

### Post by tordeu on 2011-03-25
Well, I don't know exactly what you want to achieve, but I use VirtualHosts myself. Let me just post you how I have set it up and maybe this can be of some use for you, as well.

Situation: Some of my web projects are directly on my machine and some are on a server in this network. I use VirtualHosts, so that I can easily navigate to one of my projects in the browser. For example, if I type "drupal" in my browser, it takes me automatically to my drupal-sandbox on the server.

Here is, how I have set it up:

On my machine, I have created an entry which points to the ip address of the machine which hosts the project:
```

192.168.178.36  drupal

```On my server is a similar entry, so that the server knows that "drupal" is something it is hosting itself:
```

127.0.0.1  drupal

```I have added my virtual host entries directly in the file
```

  /etc/apache2/sites-available/default

```In there, I have the entry:
```

<VirtualHost *:80>
  ServerName drupal
  DocumentRoot /var/www/sandbox/drupal/
</VirtualHost>

```That is all I did and it work. Of course, in your case you might need something different, but maybe this will help you.

EDIT: Just saw that your link basically uses the same method plus <Directory>. I need to get faster ;)

---

