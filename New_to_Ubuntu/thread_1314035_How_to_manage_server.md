---
title: "How to manage server"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by paglahaawa on 2009-11-04
I am an absolute beginner in linux.
Installed ubuntu 9.10 inside windows. 
Downloaded xampp for linux . 
Installed it.
 When i go to [http://localhost](http://localhost), it says 
**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.


When I try localhost/pohpmyadmin, it says 

**Not Found**

 The requested URL /phpmyadmin was not found on this server.
  Apache/2.2.12 (Ubuntu) Server at localhost Port 80

Please tell me where is the htdocs folder and how to access php myadmin.
Regards and thanks

---

### Post by cmnorton on 2009-11-04
I'm not sure what xampp winds up looking like. It looks like you're running Windows, not linux.

My suggestion is to tackle this in two phases. First, find the source file of the page that appeared. That will give you the default htdocs.

Then worry about loading PHP.

You need either books or internet resources -- these forums are excellent -- for configuration help, but they are written for configuring in Linux, so I'd turn to the Apache xampp group for additional information.

---

### Post by ikt on 2009-11-04
> **paglahaawa said:**
> When I try localhost/pohpmyadmin, it says 

**Not Found**

 The requested URL /phpmyadmin was not found on this server.
  Apache/2.2.12 (Ubuntu) Server at localhost Port 80

Please tell me where is the htdocs folder and how to access php myadmin.
Regards and thanks

Try using the machine ip address instead of localhost, for example for me it's:


```
192.168.1.110/phpmyadmin
```

Quick question, how did you install xampp?

---

### Post by tom.gobel on 2009-11-04
I installed Apache, PHP and MySql through Synaptic (Karmic) and everything works fine.

Apache serves pages by default from: /var/www

---

### Post by sh4d0w808 on 2009-11-04
If U plan to use phpMyAdmin, make sure that all the updates installed and your server is hardened enough - last times there are so many case-studies about hacked machines over phpMyAdmin.

---

### Post by paglahaawa on 2009-11-05
> **tom.gobel said:**
> I installed Apache, PHP and MySql through Synaptic (Karmic) and everything works fine.
 
Apache serves pages by default from: /var/www
 
Could you write down the steps please for installing it through synaptic . I have installed it through terminal, which is not fully functional.

---

### Post by paglahaawa on 2009-11-05
Could you write down the steps please for installing it through synaptic . I have installed it through terminal, which is not fully functional.

---

### Post by cmnorton on 2009-11-05
> **paglahaawa said:**
> Could you write down the steps please for installing it through synaptic . I have installed it through terminal, which is not fully functional.

Select Synaptic package manager from Administration. You'll be prompted for your password -- assuming your user set up the system -- and you'll select what you need to install, and install it.

---

### Post by MockY on 2009-11-05
> **paglahaawa said:**
> Could you write down the steps please for installing it through synaptic . I have installed it through terminal, which is not fully functional.
IMO, the absolutely easiest way of installing a webserver (at least LAMP) is via tasksel
```
sudo tasksel
```
Select LAMP and you are good to go. If you want phpmyadmin as well, then do the following
```
sudo apt-get install libapache2-mod-auth-mysql phpmyadmin
```

---

### Post by eazyigz on 2010-04-10
> **MockY said:**
> IMO, the absolutely easiest way of installing a webserver (at least LAMP) is via tasksel
```
sudo tasksel
```
Select LAMP and you are good to go. If you want phpmyadmin as well, then do the following
```
sudo apt-get install libapache2-mod-auth-mysql phpmyadmin
```

Installing phpmyadmin separately (regardless of XAMPP installation) worked for me.

---

