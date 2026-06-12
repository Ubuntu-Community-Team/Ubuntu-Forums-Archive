---
title: "endless problems...  xampp and ubuntu"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by tech7 on 2010-09-08
Okay, all together I've spend days working on trying to get things to work out..  I've even reinstalled ubuntu..
the newest issues i'm having is; 
when I power up xampp on ubuntu, I get this in my terminal
/opt/lampp/lampp: line 243: echo: write error: Broken pipe
and mysql won't work

then other problem has been going on for a while.  It is when I try to go into xampp from browser it will not go past [http://localhost/xampp/splash.php](http://localhost/xampp/splash.php), essentially it will not move past the index page..

Should I just give up???  What do you guys use to simulate webserver for development??  I need php, phpmyadmin, and mysql; that's it..  i've been having to use my windows partition when I do development and I don't think that is supposed to be the way it is...

any help, please???

---

### Post by silverglade00 on 2010-09-08
```
sudo tasksel
```

Then choose lamp server. Your web files need to go into /var/www/

After that, ```
sudo apt-get install phpmyadmin
```

---

### Post by tech7 on 2010-09-08
hey, thanks a mil, buddy..  I think you may have just got me fixed up...

---

### Post by gnicko on 2010-09-08
> **tech7 said:**
> What do you guys use to simulate webserver for development??  

We don't simulate anything...you happen to be in possession of the finest webserver in existence!

Do the real deal!

---

### Post by tech7 on 2010-09-09
> **gnicko said:**
> We don't simulate anything...you happen to be in possession of the finest webserver in existence!

Do the real deal!
what do you mean???

---

### Post by tech7 on 2010-09-09
Hey silverglade, 
I've placed my files into the htdocs folder but they aren't showing up in web-browser, I just get 404'd..  Do you know what the deal is with this???

---

### Post by tech7 on 2010-09-09
now when I startup lampp i get this in my terminal
/opt/lampp/lampp: line 125: echo: write error: Broken pipe
/opt/lampp/lampp: line 194: echo: write error: Broken pipe
/opt/lampp/lampp: line 243: echo: write error: Broken pipe
/opt/lampp/lampp: line 326: echo: write error: Broken pipe
/opt/lampp/lampp: line 137: echo: write error: Broken pipe


and my control panel shows that neither mysql or apache is running..
i'm lost..

---

### Post by silverglade00 on 2010-09-16
Sorry I have been very busy. What I had you do is install the Ubuntu version of the software instead of the LAMPP version. Your web site needs to go into /var/www/ instead of htdocs. You won't be using lampp anymore. You can check if things are running (they are by default when you run the tasksel command) by:
```

sudo /etc/init.d/apache2 status
sudo /etc/init.d/mysqld status

```

You can see the files you put into /var/www/ here: [http://localhost/]("http://localhost/")

---

