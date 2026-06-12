---
title: "NIS user login problem (ssh / gnome)"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by machu on 2007-05-25
Hi,

I have run into a problem with logging in a NIS user to a machine over ssh or logging in into gnome. 
I can easily login to a console using the NIS-username and password. But when trying to login via ssh the authentication fails. The same happens when trying to login into gnome with the NIS-username and password - it fails. 

What might be the problem? 

The NIS server is running on a FreeBSD box. The client is on Feisty. 

Any suggestions?

Regards,
Machu

---

### Post by machu on 2007-06-06
For those who will have the same problem in the future...

On the freebsd box in /var/yp/Makefile i had to uncomment the line "UNSECURE=true".

The problem is that ypcat passwd shows the hash every user's password. But on the other hand it works fine. Anyone can login via ssh or gdm.


Regards,
Machu

---

