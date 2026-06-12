---
title: "Apache to share htdocs and mysql with windows and ubuntu?"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by robembra on 2010-02-23
Hi,

I have installed xampp on my windows partition and it works fine. Now I have installed it on ubuntu and would like to share the htdocs and mysql databases from the windows partition.

I have tried chaging the httpd.conf to the path of the htdocs on my windows "/media/Shared/xampp/htdocs" and I get access is forbidden. Please could some one guide me through this???

Also the mysql databases I didnt have a clue where to start to make then shared so have not touched them :)

Thanks in advanced.

---

### Post by cariboo on 2010-02-24
You can't set permissions properly on an NTFS partition, so what you're trying to do will never work.

You can set where the mysql database files live in /etc/mysql/my.cnf. The databases themselves are located in /var/lib/mysql 

The above details are for a LAMP install, but I assume if you look in /opt you should see the same sort of file tree.

---

### Post by robembra on 2010-02-27
> **cariboo907 said:**
> You can't set permissions properly on an NTFS partition, so what you're trying to do will never work.

You can set where the mysql database files live in /etc/mysql/my.cnf. The databases themselves are located in /var/lib/mysql 

The above details are for a LAMP install, but I assume if you look in /opt you should see the same sort of file tree.


For others who wanted to do the same as me here it is...

1. Download NTFS config tool from  software center and mount your partition where htdocs/www is located.

2. Create a virtual host or use document root to point to your htdocs/www depending on the user. I changed my httpd.conf file and edited to Document Root to /media/Shared/htdocs. Then loaded [http://localhost/](http://localhost/) and it worked.

---

### Post by cariboo on 2010-02-27
You may be able to do it, but what are the driectory and file permissions? they should be either owned by root or by www-data and directory permissions should be 755. Any thing else, and you be cracked so quick you won't know what happened.

---

### Post by Rocket2DMn on 2010-02-27
It is possible to do what you are asking, but from a configurability and security standpoint, it is not advisable since you cannot control the individual file permissions at the filesystem level.  You can assign broad permissions to the entire NTFS partition using the correct mount options, but for instance, you cannot specify which files are executable and which aren't, or specify which users have particular permissions.  You may be able to get away with this without trouble, but there is always the increased level of possibility of your files or entire system becoming compromised.

---

### Post by robembra on 2010-02-28
Thanks for the advice but its just a localhost development box with everything binded to 127.0.0.1. It should be fine for this...i hope :)

---

