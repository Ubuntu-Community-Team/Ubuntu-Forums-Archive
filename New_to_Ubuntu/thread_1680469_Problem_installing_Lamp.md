---
title: "Problem installing Lamp"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by ishouvik on 2011-02-02
I am quite new on Ubuntu. Used CentOS on my VPS before though.

Ok, I have got Ubuntu Desktop version on my computer and I would like to use it as a local server as well.

I used instructions from the following links to setup Apache, MySQL, Php and PhpMyAdmin.
[http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/)
[http://docs.elgg.org/wiki/Install_Ubuntu](http://docs.elgg.org/wiki/Install_Ubuntu)

For PhpMyAdmin

> sudo apt-get install phpmyadminBut, whenever I hit the url [http://localhost/phpmyadmin](http://localhost/phpmyadmin) on my browser, I get a no found error. I have tried restarting my apache and mysql servers and followed the suggestions here [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin). But, no use.

Could anyone please help me setup my local serve? This is very very important as I am involved in web development.

---

### Post by sandyd on 2011-02-02
> **ishouvik said:**
> I am quite new on Ubuntu. Used CentOS on my VPS before though.

Ok, I have got Ubuntu Desktop version on my computer and I would like to use it as a local server as well.

I used instructions from the following links to setup Apache, MySQL, Php and PhpMyAdmin.
[http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/)
[http://docs.elgg.org/wiki/Install_Ubuntu](http://docs.elgg.org/wiki/Install_Ubuntu)

For PhpMyAdmin

But, whenever I hit the url [http://localhost/phpmyadmin](http://localhost/phpmyadmin) on my browser, I get a no found error. I have tried restarting my apache and mysql servers and followed the suggestions here [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin). But, no use.

Could anyone please help me setup my local serve? This is very very important as I am involved in web development.
link /usr/share/phpmyadmin

---

### Post by kapi on 2011-02-03
I use sudo apt-get install tasksel

It's also available in the software center.

I performed a fresh install of 10.10 three days ago and installed lamp via tasksel and it works fine.

hope this helps

---

### Post by emab on 2011-02-03
First, you must open the file
[LEFT][FONT=courier new,courier,monospace]/etc/php5/apache2/php.ini[/FONT]
[/LEFT]
and uncomment the line:
[LEFT][FONT=courier new,courier,monospace]extension=msql.so[/FONT][/LEFT]

then, you must open the file
[FONT=Courier New] /etc/apache2/sites-enabled/000-default[/FONT]
and delete the line:
[LEFT][FONT=courier new,courier,monospace]RedirectMatch ^/$ /apache2-default/[/FONT][/LEFT]

---

### Post by ishouvik on 2011-02-03
Ok thanks, guys! I will give it a shot and hopefully it resolves the issue.

---

