---
title: "Learn PHP5"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by old_dope on 2009-04-23
I want to start learning PHP. I have looked in Synaptic and PHP5 is there ready to install. But what i need is some kind person to explain in easy to understand terms how i can set up my computer to act as the server.

---

### Post by Tobi-fp on 2009-04-23
There are some great tutorials on the net, just google "php tutorial"

Else you can go download some great tutorials on the pirate bay ([www.thepiratebay.com](www.thepiratebay.com))

---

### Post by lovelyvik293 on 2009-04-23
Go and download the php manual from php.net and use it.
Or you can go to [www.w3schools.com](www.w3schools.com) for php tutorials.

---

### Post by Ms_Angel_D on 2009-04-23
If you have the cash I highly recommend the php for dummies series it's a great learning tool and has helped me immensly.

[http://www.amazon.com/MySQL-Development-Reference-Dummies-Computer/dp/0470167777/ref=pd_bbs_1?ie=UTF8&s=books&qid=1240496811&sr=8-1](http://www.amazon.com/MySQL-Development-Reference-Dummies-Computer/dp/0470167777/ref=pd_bbs_1?ie=UTF8&s=books&qid=1240496811&sr=8-1)

---

### Post by kanikilu on 2009-04-23
> **old_dope said:**
> I want to start learning PHP. I have looked in Synaptic and PHP5 is there ready to install. But what i need is some kind person to explain in easy to understand terms **how i can set up my computer to act as the server**. From your last sentence, it looks like you are wondering how to actually setup your computer as a server. The easiest way to do that is to install the "LAMP" task. You can do this one of two ways:

Terminal: ```
sudo tasksel install lamp-server
```

GUI: (Assuming XFCE here since you tagged the thread with "xubuntu") > Menu/Applications > System > Synaptic Package Manger > Edit > Mark Packages by Task > LAMP Server

In either case, pretty much the only thing you'll need to enter is a MySQL root account password.

That's it, you can now go to [http://localhost](http://localhost) in a browser to see if it's working. The webserver document root is /var/www by default.

For more information, see the following sites:

Installing the LAMP stack: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Ubuntu Server Guide: [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Apache2 Documentation: [http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

PHP Documentation: [http://www.php.net/docs.php](http://www.php.net/docs.php)

For actually *learning* PHP, I always refer to the official docs (linked above), but you can also check out the Programming sub-forum here, as well as a PHP-specific forum, such as PHPFreaks: [http://www.phpfreaks.com/forums/](http://www.phpfreaks.com/forums/)

---

### Post by old_dope on 2009-04-23
Thanks for the helpful replies everyone

---

