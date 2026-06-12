---
title: "Having a mess with apache"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by dilantha on 2010-06-03
Hi,
 Everything was started after i tried to enable .htaccess files in apache. First i did the necessary changes in */etc/apache2/sites-*enabled directory and used 
```
sudo a2enmod rewrite 
``` to enable mod rewrite.

After that when ever i click on the folder in my local host it asks to download a phtml file which is not even in that folder. 

I tried removing apache,php,mysql and reinstall them from the scratch but still i have the same problem. Please help me ](*,)

---

### Post by cariboo on 2010-06-03
Make sure you have libapache2-mod-php5 installed, that should solve your problem.

---

### Post by dilantha on 2010-06-04
> **cariboo907 said:**
> Make sure you have libapache2-mod-php5 installed, that should solve your problem.

Hi,
 Thanks for your reply. But i have already installed the libapache2-mod-php5 module :confused:. I tried to remove all the apache, mysql and php packages and download them from the beginning and install them . i got something like this when i tried to download and reinstall apache

```
Selecting previously deselected package apache2.2-bin.
(Reading database ... 213300 files and directories currently installed.)
Unpacking apache2.2-bin (from .../apache2.2-bin_2.2.14-5ubuntu8_i386.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.14-5ubuntu8_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.14-5ubuntu8_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.2.14-5ubuntu8_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Setting up apache2.2-bin (2.2.14-5ubuntu8) ...
Setting up apache2.2-common (2.2.14-5ubuntu8) ...
```Similar to other packages as well(mysql,php).I think it is not downloading apache again..instead it extracts already downloaded code previously. May be thats why stilli have the problem even i reinstall them. Please help me..

---

