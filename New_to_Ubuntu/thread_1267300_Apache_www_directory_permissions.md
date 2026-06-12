---
title: "Apache www directory permissions"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by fchieli on 2009-09-15
Hi everyone,
I just installed Ubuntu 9 server on an old computer,to practice.
I'd like to use the machine as an internal web server, with php and mysql.
Everything is installed and working (including phpmyadmin).
What's the best and secure way to setup access and permissions to the var/www directory?

I'd like to have one user (developer), being able to remotely upload files to the www directory, most likely using sftp...

Right now the permissions are set to
Owner root r w x
Group root r  x
Others r x

I was thinking about assigning the user developer to the group www-data
then set the www directory as follows
Owner www-data r w x
Group www-data r w x
Others r x

Would this be the 'proper' and secure way to set it up?
Thanks for your help
Federico

---

### Post by Diabolis on 2009-09-26
I don't think anyone can tell you which is the proper way of doing it, its your server and only you know how you want it to be used. Understanding deeply how user permissions work is what will allow you to decide by yourself wich is the best way to restrict permissions.

If only you are going to access the /var/www folder then a 700 permission will work, maybe you want others to be able to read it, so you should use 704 etc. Its up to you.

---

