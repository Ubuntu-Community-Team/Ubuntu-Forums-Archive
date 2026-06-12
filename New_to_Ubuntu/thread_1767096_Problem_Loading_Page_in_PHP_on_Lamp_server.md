---
title: "Problem Loading Page in PHP on Lamp server"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by ajwei810192 on 2011-05-25
Hi, 

  i have set up the lamp using sudo tasksel, and i do see the html pages running properly when I go to [http://localhost/](http://localhost/). The problem is, when I start testing the php configurations, I do see that php -v is installed, and it is, 

PHP 5.3.5-1ubuntu7.2 with Suhosin-Patch (cli) (built: May  2 2011 23:00:17) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies
[B]
When I run the phpinfo page, it tells me 

[/B]Unable to connect
  Firefox can't establish a connection to the server at 127.0.1.1.
 
 The site could be temporarily unavailable or too busy. Try again in a few
    moments.
  If you are unable to load any pages, check your computer's network
    connection.
  If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.[B]

I did open up the ports for 80 on both udp and tcp. What is wrong with my settings? 

Thanks for your help.
[/B]

---

### Post by Wim Sturkenboom on 2011-05-25
What did you enter in the address bar ?

And where is the file stored that contains the phpinfo?

---

### Post by aeiah on 2011-05-25
127.0.1.1?

did you mean 127.0.0.1 (ie, localhost)?

---

### Post by ApOgEEs on 2011-05-25
127.0.1.1 will also works when you have it in /etc/hosts

Have you enable your php for apache?
If not, you can enable it by this command:
```
$ sudo a2enmod php5
```

Have you restart your apache server?
After enabling the service, you can restart your apache using this command:
```
$ sudo service apache2 restart
```

Then, try again with your browser.

---

### Post by Wim Sturkenboom on 2011-05-26
> **aeiah said:**
> 127.0.1.1?

did you mean 127.0.0.1 (ie, localhost)?good catch ;)

---

### Post by ApOgEEs on 2011-05-26
> **aeiah said:**
> 127.0.1.1?

did you mean 127.0.0.1 (ie, localhost)?

I don't see that as an issue since my ubuntu also have this entry in /etc/hosts:
```
127.0.0.1   localhost
127.0.1.1   myubuntubox
```

---

