---
title: "Help with LAMP server"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by econstant on 2010-10-13
I just created a LAMP server VM  as follow:

Host OS: Ubuntu desktop 10.04
VM app: VirtualBox
Guest OS: Ubuntu Server 10.04

Commands for LAMP install:
[http://mixeduperic.com/linux/how-to-install-lamp-phpmyadmin-and-collabtive-on-ubuntu-1004-server.html](http://mixeduperic.com/linux/how-to-install-lamp-phpmyadmin-and-collabtive-on-ubuntu-1004-server.html)
and

[http://roberttrevellyan.blogspot.com/2010/10/web-developer-testing-server-setup.html](http://roberttrevellyan.blogspot.com/2010/10/web-developer-testing-server-setup.html)

Commands for ufw setup:
[http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server](http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server)

I'm receive this error when i attempt to connect to phpmyadmin from my host OS web browser:

=======================================================
Unable to connect

Firefox can't establish a connection to the server at 192.168.1.106.
       
    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web
=======================================================

My goal is to setup a LAMP VM so i can learn how to PHP/MySQL.  I want to be able to develop on my host OS and upload files to the guest OS to view from my host OS.

Can someone help me please?

---

### Post by Blasphemist on 2010-10-13
If you disable ufw does the browser connect? Check the phpMyAdmin configuration if you need but looking at the documentation you followed my guess is that the port needed, by default 8080, is blocked. This is the phpMyAdmin wiki page- [http://wiki.phpmyadmin.net/pma/Config](http://wiki.phpmyadmin.net/pma/Config)
The section at the top of that page, PmaAbsoluteUri, discusses the config for the access you desire I believe.

I just installed Apache, MySQL, php and Drupal on my laptop for much the same reason since I didn't have another machine to use. I intend to find one and do this so I'm anxious to know how this comes out for you.

---

### Post by cavh on 2010-10-13
By far the easiest way to install a LAMP server is to run 

```
sudo taskel
```

in  a terminal and choose the LAMP option using your keyboard's space bar to tick the box. Do ***not*** untick any of the other boxes which are marked, as you may inadvertently uninstall your GNOME/KDE desktop and do other horrible things.

---

### Post by CharlesA on 2010-10-13
Make sure you are using bridged networking instead of NAT.

---

### Post by econstant on 2010-10-13
why is  taskel needed?
sudo taskel

---

### Post by AndyM3 on 2010-10-13
> **cavh said:**
> By far the easiest way to install a LAMP server is to run 

```
sudo taskel
```

in  a terminal and choose the LAMP option using your keyboard's space bar to tick the box. Do ***not*** untick any of the other boxes which are marked, as you may inadvertently uninstall your GNOME/KDE desktop and do other horrible things.

That would be "sudo tasksel", if I am not mistaken.

---

### Post by econstant on 2010-10-14
OK I created a new Ubuntu server VM machine.  During the Server OS install, I picked LAMP Server and OpenSSH Server to be installed.  After the Server OS install, I installed phpmyadmin, ufw, nano, wget.

I tested and was able to see 'phpinfo()' on my Host OS browser. Also, I was able to login to phpmyadmin as well so these work.

Now, I want to be able to create domains and subdomain I as I learn php and mysql.  My question is how do i do that?  For example:

localhost/Chapter1/project1/index.php
localhost/Chapter1/project2/index.php
localhost/Chapter2/project1/index.php
localhost/Chapter2/project2/index.php

etc .....
Also with ufw how do I setup ufw so i don't lose host OS browser access to php, mysql and apache?  I didn't enable ufw yet because I feel I might have set it up wrong in my last install.

---

### Post by CharlesA on 2010-10-14
You'd need to create those folders in /var/www/

---

### Post by lexdave on 2010-10-14
That will be done in apache2, called virtual directories.  You can map a folder either to domain names or IP address (so that when you go to test.com it will send you to the folder /var/www/html/test/index.php), phpadmin does the same thing (and you will see its virtual directory settings).  You have to look-up how to do that on Ubuntu as I usually use fedora/centOS as my web-server of choice, and it is slightly different(but I cut my teeth on Ubuntu).

---

### Post by econstant on 2010-10-14
Thanks CharlesA, it works now.  Now that everything is work right.  How do I set up ufw to security without out screwing up the Host OS access to the webserver?

---

