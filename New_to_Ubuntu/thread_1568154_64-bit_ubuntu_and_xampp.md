---
title: "64-bit ubuntu and xampp"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by tech7 on 2010-09-04
I'm a noob to ubuntu..  So thank you for your patience..

I've followed two, maybe three tutorials and can't quite get things worked out..

Has anybody had a successful install of xampp on ubuntu 10.01.4 lucid 64-bit?????
If so, how did you do it??
Thanks.

---

### Post by sandyd on 2010-09-04
> **tech7 said:**
> I'm a noob to ubuntu..  So thank you for your patience..

I've followed two, maybe three tutorials and can't quite get things worked out..

Has anybody had a successful install of xampp on ubuntu 10.01.4 lucid 64-bit?????
If so, how did you do it??
Thanks.
XAMPP is just made up of **A**pache,**M**ySQL,**P**hp,**P**erl

You can run```

sudo apt-get install apache2 php5 mysql-server
```
to install apache, php, and mysql.

---

### Post by Christian Knudsen on 2010-09-05
I've got Apache, MySQL, PHP and Perl installed on my 10.04 64-bit laptop. It works perfectly. I think I just used this guide:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by indytim on 2010-09-05
```

$ sudo tasksel

```

Select the LAMP option (space bar) and sit back and let the app do the heavy lifting for you.  It's definitely an "Easy Button". :p

-IndyTim / DataMan

---

### Post by tech7 on 2010-09-08
Hey cool, guys!!
I uninstalled my xampp and installed the stuff carlee was talking about..  I just couldn't get xampp to work out, maybe it's an isolated issue with some configuration on my computer, i'm using wubi...


Hey Carlee; do you know where they may be some instructions about how to use these utilities, i'm assuming there's no control panel and i'll be using terminal to start them up and whatnot, right???

thanks.

---

### Post by gnicko on 2010-09-08
You should look up a beginning PHP reference book or online tutorial. Most beginner PHP books will walk you thru setting up a LAMP server and how to get it running/using it to start learning how to build websites. (Probably on Windows, tho.) Your best buddy is Google.

But it sounds like you've got things pretty much set up already. If you followed the step(s) above, you should be good-to-go. The webserver (Apache) and PHP, MySQL, etc. should start up automagically when the O/S starts, but there are other ways to set it up.

Your websites/development projects, etc. should use /ver/www/ as the site root by default. If you make an index.html file, it goes there. Then browse over to [http://localhost/](http://localhost/) and you should see it if Apache is working properly. 

Here's a couple of things you can do to confirm all is well:

1) Make a text file in /var/www/ and name it info.php.
2) Put this code in it:
```
<?php phpinfo(); ?>
```
3) Point your browser to [http://localhost/info.php]("http://localhost/info.php") 

If all goes well, and PHP installed correctly, you should see all the information for the PHP installation on your webserver. (Basically we're looking for a blue and white screen with lots of information right now. Worry about what it says later on.)

4) Then, if that works navigate to:[ http://localhost/phpmyadmin]("http://localhost/phpmyadmin") and you should see the login page for your MySQL server.

Its that simple.

If these steps don't work, look this over: [http://www.howtoforge.com/ubuntu_lamp_for_newbies]("http://www.howtoforge.com/ubuntu_lamp_for_newbies")

...Or, if you don't like that one, there are bunches of them by Google-ing "LAMP server howto" or similar.

Good Luck!

---

### Post by sandyd on 2010-09-08
> **tech7 said:**
> Hey cool, guys!!
I uninstalled my xampp and installed the stuff carlee was talking about..  I just couldn't get xampp to work out, maybe it's an isolated issue with some configuration on my computer, i'm using wubi...


Hey **sandyd**; do you know where they may be some instructions about how to use these utilities, i'm assuming there's no control panel and i'll be using terminal to start them up and whatnot, right???
[B][http://webmin.com](http://webmin.com) should give what you want :D.
Just make sure you firewall the port that webmin runs on so that the control panel is not accessable to the world.
:)
[/B] thanks.
gl

---

