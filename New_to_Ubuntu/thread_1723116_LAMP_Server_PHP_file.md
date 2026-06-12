---
title: "LAMP Server PHP file"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by cwick on 2011-04-06
Recently setup LAMP server and I must have missed a step because I cant seem to save a php file in my root directory and call it up on the server? Anyone have any suggestions?
 
Thanks

---

### Post by alphacrucis2 on 2011-04-06
> **cwick said:**
> Recently setup LAMP server and I must have missed a step because I cant seem to save a php file in my root directory and call it up on the server? Anyone have any suggestions?
 
Thanks

Shouldn't this go in /var/www ? That's where apache will be looking for files by default IIRC.

---

### Post by lisati on 2011-04-06
> **alphacrucis2 said:**
> Shouldn't this go in /var/www ? That's where apache will be looking for files by default IIRC.

Agreed. What I usually do on my server is to use ftp or samba to place a copy of the file in question on my server, then SSH into the server, and use something like **sudo cp */path/to/file* /var/www** to copy it from where I saved it to the publicly accessible area.

---

### Post by cwick on 2011-04-06
pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }  Thank you. When I go make a **phpinfo.php** file and save that in /var/www I still come up with nothing on tthe server. I use [*sudo gedit /var/www/phpinfo.php*] to write my example code in this file
 <?php phpinfo(); ?>

[FONT=Verdana]Just think I'm missing a step or not saving it in the correct directory?

Any instructions on how to do this would be greatly appreciated ...
[/FONT]

---

