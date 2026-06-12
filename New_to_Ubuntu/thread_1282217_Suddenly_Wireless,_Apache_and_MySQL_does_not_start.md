---
title: "Suddenly Wireless, Apache and MySQL does not start on boot"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by Vulgarian on 2009-10-04
I installed Linux on to my Acer Travelmate 4270 notebook. Everything worked fine. I even got Apache web server, PHP and MySQL working. Suddenly Shutdown did not work. After a few attempts of failing to switch the machine off, I removed all source of power. Now Apache, MySQL and Wireless does not work on boot. Can somebody please help. I am new to all of this Ubuntu and LAMP stuff.

---

### Post by crolanx on 2009-10-04
You need to make sure that the services for Apache & MySQL are enabled. Just navigate to **/etc/rc2.d/** and see if there are entries with *apache* oder *mysql* in the filename.

For wireless networking, at least the service *networking* is necessary, but I don't know if you need any further services for WiFi.

---

### Post by Vulgarian on 2009-10-04
Thanks for your help crolanx. 

Sorry I'm new to this. When you say "entries" you mean file names ?

---

### Post by crolanx on 2009-10-04
Yes, i meant the files in the folder when I said entries

But i'll try to explain it a little bit more detailed:

There are many ways to examine which services are enabled.

The simples one is to check, whether the so called symlink for the service exists in **/etc/rc2.d/**. The symlinks points to a script in **/etc/init.d/** which starts the service.

To be sure that the symlinks for Apache and MySQL exist, you can use nautilus and navigate to the folder **/etc/rc2.d/**. There you look at the filenames and check if there are any files with *apache* or *mysql* in the filename.

e.g. my entry for Apache looks like this: **S91apache2**
The symlink for MySQL may be: **S80mysql**
and the service for the networking is called **S40networking**

Plese note, that the number at the beginning can differ.

If theese entries for Apache, MySQL and networking do not exist, the services will not be started during boot. We then would need to enable those services by creating a symlink.

---

### Post by antony.s on 2009-10-04
Or if you prefer using the GUI, you could try System -> Administration -> Services and see if Web Server (apache) and Database Server (mysqld) are ticked

If they are not, unlock with your superuser password and tick them

---

