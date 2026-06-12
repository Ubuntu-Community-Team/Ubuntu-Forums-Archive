---
title: "[SOLVED] configure LAMP to work offline?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by minsf on 2009-01-10
hi,
just installed lamp (via "tasksel install lamp-server").
i only need it for developing; that is, i check my php scripts by pointing firefox to [COLOR="Blue"]localhost/script.php[/COLOR].
[COLOR="Red"]how do i make this work offline?[/COLOR] (that is, when i have no internet connection) my guess is i'm going to have to play with the loopback interface somehow...
needless to say i'm a lamp-newbie, so any [COLOR="Red"]advice regarding configuration[/COLOR] (for developing) will be highly appreciated, as well as any [COLOR="Red"]link to beginners' apache guide[/COLOR] (i don't know where to start swimming in the ocean of documents on apache.net, and most other google results i got so far discuss installations mainly).
thanks :)

---

### Post by jfr1tz on 2009-01-10
in /etc/hosts localhost is defined as 127.0.0.1 which is your loopback interface. so localhost should work for you with and without an active internet connection.

---

### Post by ifthengoto on 2009-01-10
You may want to only allow local connections to your server if you are just using your computer as a development machine otherwise you will have security risks.

Change the listen directive to only listen to localhost.

> sudo nano /etc/apache2/ports.confand change the Listen line to this

> Listen 127.0.0.1:80

Restart apache

> sudo /etc/init.d/apache2 restartthen surf to 

> [http://localhost](http://localhost) or
> [http://127.0.0.1](http://127.0.0.1)

---

### Post by Joeb454 on 2009-01-10
It should work fine without a network connection :confused:

if it doesn't then the steps above should make it work as you want anyway :)

---

### Post by minsf on 2009-01-10
just a guess: maybe it is a problem on the firefox part; i mean, maybe when firefox starts and cannot connect to google, it goes into offline mode until i have a new connection, and wouldnt even display the localhost. 

here are more details about the prob: my /etc/hosts defines localhost correctly (i have a line "127.0.0.1 localhost"). apache is started (via "sudo /etc/init.d/apache2 restart"). i am not connected to the internet (sitting in a coffee shop with no network). i start firefox and point it to localhost or to [http://127.0.0.1](http://127.0.0.1) and get nothing. then i connect to the internet (i come back home). refresh the page and get the "it works". now when i disconnect from the internet i will get the "it works" page, but i think it is just the cache.

regarding the ports.conf suggestion: here is my current file
```
NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```
so should i just change the second line to "Listen 127.0.0.1:80"?
can i safely remove all the SSL lines?
thanks!

---

### Post by ifthengoto on 2009-01-10
Just change the second line 

> Listen 127.0.0.1:80

---

### Post by JKHinton CPBD on 2009-01-10
I had this same problem Minsf, I was trying to use my laptop to continue working on my LAMP website in a location with no internet service.  All I had to do was check or uncheck the work offline in the firefox web browser under the file tab. This allowed me to run web pages through localhost.

---

### Post by minsf on 2009-01-10
thanks james
when the firefox starts and cant find a connection it indeed went into offline mode, and no refresh helped. but unchecking the "file>work offline" and refreshing made it work. 

any idea how to disable firefox's auto offline mode?

---

### Post by MattyGabe on 2009-03-30
> **minsf said:**
> thanks james
when the firefox starts and cant find a connection it indeed went into offline mode, and no refresh helped. but unchecking the "file>work offline" and refreshing made it work. 

any idea how to disable firefox's auto offline mode?
--Bump--

I too have had this problem for months now on my Xubuntu box that I sparingly use (hence why it took me so long to look for a solution again).  Firefox indeed sets itself into offline mode when it starts up and has no internet connection, therefore I cannot view the localhost server that I have LAMP running on (I use the OSS software called PHPPOS on the machine, and have no internet connection for the isolated machine).  Sure, you can go to File -> Uncheck Offline Mode, but that's really annoying when all you want it to do is start when you power the computer on.

Anyone know how to do this?  I've tried looking in FF's about:config, but any of the settings previously suggested haven't worked.  Any help here would be greatly appreciated, thanks!

---

### Post by kanikilu on 2009-03-30
Try changing browser.offline-apps.notify to false in about:config.

If that doesn't work, there is a firefox add-on that will put a button in your status bar. I think it just mimics the behavior of File > Work Offline, but is a little faster to get to...

[https://addons.mozilla.org/en-US/firefox/addon/493](https://addons.mozilla.org/en-US/firefox/addon/493)

---

