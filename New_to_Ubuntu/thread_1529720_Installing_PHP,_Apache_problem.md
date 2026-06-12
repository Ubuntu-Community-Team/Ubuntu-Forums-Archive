---
title: "Installing PHP, Apache problem"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by cordnor on 2010-07-12
Hi
 I am new to Ubuntu I have installed 10.04
 I want to install separatly MySQL, Apache, PHP and Drupal for testing.
 I have successfully installed MySQL
 

 In Synaptic Package I find Apache2,2-binwhih inform me:

 *This package contains all binaries but no configuration or support scripts. *
 *To get a stand-alone server, you need to install one of the apache2-mpm-* *
 *packages, such as worker or prefork. Other packages like gnome-user-share *
 *may bring their own Apache configuration, though.*
 

 Where do I find the apache2-mpm-packages?   
 Do I have to download Apache from apache.org and install?
 

 I can not find PHP. Do I have to download PHP from php.org and install?


Anyone who can help a newbe

---

### Post by cariboo on 2010-07-13
Seeing as you are a new user, it would be much easier if you installed the LAMP stack (**L**inux, **A**pache, **M**ysql, **Ph[**).

Go to System->Administration->Synaptic Package Manager->Edit->Mark packages by task, and select LAMP for install.

You can also intall it via the command line:

```
sudo tasksel
```

---

### Post by cordnor on 2010-07-13
> **cariboo907 said:**
> Seeing as you are a new user, it would be much easier if you installed the LAMP stack (**L**inux, **A**pache, **M**ysql, **Ph[**).

Go to System->Administration->Synaptic Package Manager->Edit->Mark packages by task, and select LAMP for install.

You can also intall it via the command line:

```
sudo tasksel
```

Hi and thanks for your reply:
Just for fast coming up for test I did use LAMP:

  	 	 	 	 	 	  Installed the LAMP stack (**L**inux, **A**pache, **M**ysql, **Ph[**)
 System->Administration->Synaptic Package Manager->Edit->Mark packages by task>LAMP server
 

 During installation you can choose to see the details, but not copying them so you can learn what is done during installation. _**This should be possible.**_
 

 Installing drupal
 System->Administration->Synaptic Package Manager->Search
 drupal6
 configuring drupal6 I chose configure database for drupal6 with dbconfig-common
 _**Again not possible to copy details, which should be possible (to see what is done)**_
 

 in terminal I checked if the database was created and found drupal6 but no tables.
 In /usr/share/doc/drupal6/examples I found README.Debian.gz
 In #3 Database population script:
 [http://localhost/drupal6/install.pnp](http://localhost/drupal6/install.pnp)
 

 did that in firefox with result:
 NOT FOUND
 The requested URL /drupal6/install.php was not found on this server.
 

 What now????
 Is there any tutorial for this?

---

