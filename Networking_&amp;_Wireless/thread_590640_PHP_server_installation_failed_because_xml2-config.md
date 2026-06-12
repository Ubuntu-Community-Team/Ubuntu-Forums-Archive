---
title: "PHP server installation failed because xml2-config not found"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by sshahir on 2007-10-24
Hello ,

After installing Apache http Server 2.2.6, I tried to install PHP server 5.2.4; however, I am runing into installation error:

[COLOR="Red"]
error: xml2-config not found. Please check your libxml2 installation.[/COLOR]

Based on the  [COLOR="Blue"][[COLOR="Blue"]_thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=389919&highlight=PHP+xml2-config")[/COLOR] to work-around the issue, the libxml2-dev package has to be installed.

Therefore, I downloaded the libxml2-dev package, but when I try to install the package, package installer is thrown the error below(please see the attachement).

[COLOR="Red"]Error: Dependency is not satisfiable: libxml2[/COLOR]

First time when I had encountered the error message during installing the libxml2-dev,I checked my synaptic manager and libxml2 was already installed. I re-installed the libxml2 package which causes the package broken:(. After installing the libxml2 package, my Ubuntu OS is cashed:oops:, and I had to format the partitions and reinstall the OS:mad::mad:.

Now after reinsalling the ubuntu OS 6.0.6 and Apache http Server 2.2.6, I am runing to the same error during the PHP server 5.2.4 installation.

[COLOR="Red"]error: xml2-config not found. Please check your libxml2 installation.[/COLOR]

To work-arond the error, I am trying to insall the libxml2-dev package, and thepackage installer is thrown the same error:

[COLOR="Red"]Error: Dependency is not satisfiable: libxml2[/COLOR]

At this point, the following three questions come to my mind.

[COLOR="DarkRed"]   1.      How to install xml2-config?
   2.      Is the installation of the libxml2-dev package the right solution to work-around the PHP installation error?
   3.      If it is, please let me know how should I install the libxml2-dev package without runing into the " Dependency is not satisfiable: libxml2" error message?[/COLOR]

I appreciate for any answers, comments, or solutions.

sshahir

---

### Post by sshahir on 2007-10-25
any suggestions?

---

### Post by conjur3r on 2007-10-25
How did you install apache and php?  From source or using the packages?

---

### Post by az on 2007-10-25
If you are trying to install from the repositories, make sure that you do not have mixed sources in your list - that it, make sure that all your entries point to the same release of Ubuntu and you have no other external repos enabled.  The software is compatible at the source level, not the binary level.

then run

sudo apt-get update

and 

sudo apt-get -f install

and then try again to install.

---

### Post by sshahir on 2007-10-25
> **conjur3r said:**
> How did you install apache and php?  From source or using the packages?
I have downlaoded, and unpacked  Apache and Php from their websites and installed them using the [[COLOR="Blue"]instructions[/COLOR]]("http://www.php.net/manual/en/install.unix.apache2.php") provided on Php documentation page.

Any suggestion?

---

### Post by sshahir on 2007-10-25
> **az said:**
> If you are trying to install from the repositories, make sure that you do not have mixed sources in your list - that it, make sure that all your entries point to the same release of Ubuntu and you have no other external repos enabled.  The software is compatible at the source level, not the binary level.

then run

sudo apt-get update

and 

sudo apt-get -f install

and then try again to install.

Do you mean I cannot install the Apache and Php servers from their sources, and I have to use repositories?

---

### Post by conjur3r on 2007-10-25
No, you can still download the versions found on their site but for simplicity, it's ALOT easier to install apache and php with the following:

# sudo apt-get install apache2 php5

This will install everything it needs to run the applications, and it won't require any development packages (perfect for hardening your server).

With compiling from source, you need to make sure that you satisfy all dependencies yourself and as you have found, it's not always that easy.  In a lot of cases, you will probably require strict versions of libraries which add to the complication.  Also, sometimes the libraries are installed in strange places so you may need to feed the path into your ./configure command.  Try **./configure --help** for more information.

---

### Post by az on 2007-10-25
> **sshahir said:**
> Do you mean I cannot install the Apache and Php servers from their sources, and I have to use repositories?

You don't have to, but there is no compelling reason to no do so.

The advantage of using the repos is that you get proper support.  If there is a security or bug fix, you will get it almost effortlessly.  This is not so if you install from source.

You can do what you want, but I do not recommend installing such core components of your server from source.

---

### Post by sshahir on 2007-10-26
I have successfully been able to run the "sudo apt-get install apache2 php5" command.

After executing the above command, I have tried to brows to "http://localhost", and the page (index.html) opened which shows that Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80 have been installed. However, when I look at /usr/local/apache2/htdocs, I couldn't find the corresponding index.html file. Do you know where the index.html is located?

---

### Post by conjur3r on 2007-10-26
/usr/local/apache2 is what you installed from your sources.  You can remove them now as  you are now using the Ubuntu packaged version.

Your htdocs location is in **/var/www/**.  You apache configuration files are in **/etc/apache2** and your php5 configs are **/etc/php5**

---

### Post by az on 2007-10-26
> **sshahir said:**
> I have successfully been able to run the "sudo apt-get install apache2 php5" command.

After executing the above command, I have tried to brows to "http://localhost", and the page (index.html) opened which shows that Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80 have been installed. However, when I look at /usr/local/apache2/htdocs, I couldn't find the corresponding index.html file. Do you know where the index.html is located?

You need to install the apache2-doc package.

---

### Post by sshahir on 2007-10-26
Thanks for the information

I have also installed the php5-cgi to run the php scripts, and then restart the apache server:
> sudo /etc/init.d/apache2 restart

I have verified that both the /etc/apache2/mods-enabled/php5.conf and /etc/apache2/mods-enabled/php5.load  file exist.

However, I still cannot run any php scripts. Is there any ways to restart php server? Any suggestion?

---

### Post by conjur3r on 2007-10-26
You do not need php5-cgi unless you want to run PHP as a CGI module which is normally not the case.  This provides the php5 fastcgi version and treats php scripts like cgi scripts (ie all of your php5 scripts will require execute permissions).

I believe apache is getting confused with which php libraries to load.  Have you completely removed the compiled versions you installed from source?

On my machine, I only have the following php packages installed:

# dpkg -l | grep php
ii  libapache2-mod-php5                        5.2.3-1ubuntu6                       server-side, HTML-embedded scripting languag
ii  php5                                       5.2.3-1ubuntu6                       server-side, HTML-embedded scripting languag
ii  php5-common                                5.2.3-1ubuntu6                       Common files for packages built from the php

Try creating the following file **/var/www/test.php** with the following contents:

<?php
phpinfo();
?>

Then open up your browser and go to [http://localhost/test.php](http://localhost/test.php)

Also, all you need to do to get the latest changes to your php configuration is to restart apache.  There is no php server.

---

### Post by sshahir on 2007-10-27
Hello **conjur3r** and **az**

I appreciate for your valuable comments and suggestions through out the PHP installation.

I was wondering whether the apache document root would be the  the &#8220;/var/www/apache2-default&#8221;  or &#8220; the &#8220;/var/www&#8221; folder. 
Because I found the only index.html.en file in  the &#8220;/var/www/apache2-default&#8221; folder, I thought the folder is the apache document root, and I created an .php script file in the &#8220;/var/www/apache2-default&#8221; folder with the same permission as the index.html.en file (644). After I moved the .php file into the &#8220;/var/www&#8221; folder and changed its permission to 755, as you mentioned, I have been able to browse through my PHP scripts successfully. Thank you.

Cheers,
sshahir

---

