---
title: "[SOLVED] Noob needs help setting up a website server"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Papa_Bear on 2008-12-05
Hi! :D  I'm trying to set up my workstation, which has Ubuntu 8.04 desktop ed. installed, into a webserver. I installed Apache2, MySQL, and PHP using:

```

sudo apt-get install apache2
sudo apt-get install mysql-server
sudo apt-get install php5

```

Now how can I go about and test if I installed the three properly?
The web space of apache is on */var/www* right? But I can't put my files there.

By the way, I'm a noob in Ubuntu so please be considerate... :)

---

### Post by silverglade00 on 2008-12-05
type sudo tasksel and pick lamp server. it will do it all for you.

---

### Post by Papa_Bear on 2008-12-05
Ok, I did sudo tasksel and picked the lamp server.
Where should I put my php files? I tried forcefully putting my test php files on /var/www using sudo but when I click it, all that happens is that firefox regards it as a downloadable file. The index.html file inside it works though. :???:

---

### Post by m_duck on 2008-12-05
If you type ```
http://localhost/pagename.php
```into firefox, it should load it properly. I think it probably just tries to load the file when you click on it, rather than it getting processed first.

---

### Post by Papa_Bear on 2008-12-05
I tried that but it did the same thing as when I clicked it. Do you think there is something wrong in the way I installed it?

---

### Post by Locke_99GS on 2008-12-05
It's not being interpreted. Make sure PHP is enabled correctly in the apache configuration.

---

### Post by adityakavoor on 2008-12-05
apt:libapache2-mod-php5

---

### Post by Papa_Bear on 2008-12-05
I know that this is a very noobish question... but how do I enable PHP in the apache configuration... :?:?

---

### Post by Locke_99GS on 2008-12-05
Try this - skip the compiling if you have already have binaries.
[http://www.petefreitag.com/item/516.cfm](http://www.petefreitag.com/item/516.cfm)

---

### Post by snova on 2008-12-05
Ubuntu Server Guide: [http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

There is also: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

But it appears a bit outdated.

---

### Post by thunderbirdje on 2008-12-05
Greetings

I installed LAMP with help of Synaptic Package Manager (under System > Administration).

Then you can click "Edit" > "Mark packages by task".

Do a search to "LAMP"

Install...

And all the configuration is done for you! With a GUI!

btw: /var/www is only accessable by the user who is owning that directory! You can change the owner (do a search for chown)... But I do not now if that is safe? I always run "gksudo nautilus" which gives you a browers with ROOT rights! **Be carefully, with root rights you can delete/erase everything on your harddisk!!! Use it with care and a clear mind**

Good luck!

---

### Post by Papa_Bear on 2008-12-09
Alright! I've done what you guys said and everythings up and running now. Thanks!!!:guitar:

---

