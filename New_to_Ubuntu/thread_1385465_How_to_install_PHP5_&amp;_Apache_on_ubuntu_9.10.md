---
title: "How to install PHP5 &amp; Apache on ubuntu 9.10"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Edgar09 on 2010-01-19
Iam a newbie on linux & on PHP so please help me
How can i install php5 and Apache on ubuntu 9.10? I tried doing it on the terminal 

    sudo apt-get install apache2

    sudo apt-get install php5

    sudo apt-get install libapache2-mod-php5

    sudo /etc/init.d/apache2 restart

But when i check on the Main Menu i dont see the php5 nor apache
Or is there anything else i need to do or is there any other program  similar on linux?

---

### Post by bodhi.zazen on 2010-01-19
Neither apache or php will be listed in your desktop menu.

If you open your browser and go to

[http://localhost](http://localhost)

You should see the infamous "It Works !"

IMO, if you want a graphical interface for your server, use one of the many web based ones rather then gnome

I advise webmin

---

### Post by sandyd on 2010-01-19
p.s. you will be asking this later, so i might as well tell you now that your webserver root is in /var/www
you will need elevated permissions to copy there though.

so for example, if you want [http://mysite.com/test.html](http://mysite.com/test.html)
you would put test.html in /var/www

---

