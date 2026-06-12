---
title: "Apache2: port 80 unavailable?"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by flummoxed on 2007-03-02
I've been slowly figuring out what apache, php, and mysql are, as I've been trying to set them up so I can learn php and mysql. I have everything installed, but php still isn't working. My browser tries to download the php file instead of running it. I have all the files this guide told me to install: 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I tried this code to get the php working: 

```
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

I get this output:

```
allan@ubuntu:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                   (98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```

I heard skype can take up port 80, but I don't have it installed. What other programs might be using this port?

---

### Post by godsyn on 2007-03-02
I recently had this issue and was suprised that i had already ran apache2.. make sure the service (or the stand alone) isn't already running.

---

### Post by flummoxed on 2007-03-02
Well I know that apache is working now, because I can get to teh apache test page fine. But php is still not working, and I don't know what is wrong.

---

### Post by Floppyjoe on 2007-03-03
Try installing *[COLOR="red"]libapache2-mod-php5[/COLOR]* if you don't have it installed.
Then run the following:
```
sudo a2enmod php5
```
along with:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by Gerard Barberi on 2007-03-03
I had a similar problem once.  Try installing php-pear.

EDIT:  And then restart apache2

sudo /etc/init.d/apache2 restart

---

### Post by flummoxed on 2007-03-03
I've done all the things you guys mentioned... it says php5 is enabled. Still no dice. The apache server works, but php doesn't. also, when I try to run mysql, I get this: 

```
ERROR 1045 (28000): Access denied for user 'allan'@'localhost' (using password: NO)

```

This is annoying. I have all this working on windows, but I'd prefer to be using ubuntu than xp while developping.

---

