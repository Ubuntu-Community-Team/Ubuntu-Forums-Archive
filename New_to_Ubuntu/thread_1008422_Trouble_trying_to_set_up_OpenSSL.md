---
title: "Trouble trying to set up OpenSSL"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Spunkbubble on 2008-12-11
First off, I'm a total beginner here. My only real past experience doing anything non-GUI beyond a basic level with any Linux system was troubleshooting installing a wireless device (which failed failed miserably despite the help of some experienced users, and a guarantee on the box that it was Linux-compatible). Even then I was just executing commands that were instructed - I understood only a few. So warning over, just bear this in mind =)

I want to install OpenSSL. But unfortunately, the process has really gone tits-up and now I'm missing a load of directories/files etc now I've come to the point of actually getting it running after installation. So I have bits and pieces of the installation, but gaping holes where some stuff should be. All I've done is follow some different online tutorials and instructions, and manually work around any small problems up until this point.

As this clearly isn't working for me, I'd really appreciate it if someone could help out with a step-by-step guide on how I'm meant to get it working (and how to use it once installed if possible) - trying to figure it out from an online tutorial which I don't fully understand hasn't worked for me. It's helpful especially if the process is explained - I don't want to be a noobie forever so the more I understand what I'm doing and why, the better. I suppose to start with some help on how to uninstall all the crap I've accumulated and data I've put in that now I need to get rid of.

Thanks in advance for any help =)

---

### Post by Sarmacid on 2008-12-11
I got it working after installing apache2 from the repos and following the guide at [https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

The guide for 7.10 worked for me, even tho I did it on 8.04, you should start from ```
sudo apt-get install apache2
``` till it says Ubuntu 7.04

If you have any questions, post them here.

---

### Post by Spunkbubble on 2008-12-11
First off, thanks for the response. =)

Having followed the instructions on the link you gave, I've successfully got up to the point "Restart Apache server" where executing the supplied command returns:

```
 * Restarting web server apache2                                                                                                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Dec 11 19:41:37 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Dec 11 19:41:37 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Dec 11 19:41:47 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Dec 11 19:41:47 2008] [warn] NameVirtualHost *:80 has no VirtualHosts

```

Trying to use the "Old fashioned way" just gives a "command not found" error straight away.

I'm not entirely sure what I've done wrong since I've tried to follow the instructions as precisely as I can. However, I didn't understand some of it so it's possible I messed up.

---

### Post by Sarmacid on 2008-12-11
Post the output of```
head /etc/apache2/sites-available/default
```
And
```
head /etc/apache2/sites-available/ssl
```

---

### Post by Spunkbubble on 2008-12-11
Results are:

```
NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>

```

and

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>

```

---

### Post by Sarmacid on 2008-12-11
Here's the problem
> **Spunkbubble said:**
> 
```
NameVirtualHost *
<VirtualHost *>

```

Change it to ```
NameVirtualHost *:443
<virtualhost *:443>
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem

```

---

### Post by Spunkbubble on 2008-12-11
Ok done that, now trying to reload returns:

```
apache2: Syntax error on line 298 of /etc/apache2/apache2.conf: Syntax error on line 2 of /etc/apache2/sites-enabled/000-default: /etc/apache2/sites-enabled/000-default:2: <virtualhost> was not closed.
   ...fail!

```

Why is this? It looks to me as if "virtualhost" is enclosed properly in <> with its value. Does it not work this way?

---

### Post by Sarmacid on 2008-12-11
You should look around for a missing </virtualhost> tag after a <virtualhost> tag.

---

