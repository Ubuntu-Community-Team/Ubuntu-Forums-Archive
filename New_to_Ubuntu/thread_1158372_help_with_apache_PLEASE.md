---
title: "help with apache PLEASE"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by philcamlin on 2009-05-13
hi im new to the forums but
when i go to my site 
all i get is a index page 
where do i put my files to host them ???

:popcorn:

---

### Post by OffAxis on 2009-05-13
put them in the /var/www/ folder.

index.html is the first file that apache looks for (the default page).

index.php, index.php3, and some other variations also work (there's a hierarchy specified in one of the config files)

---

### Post by Iowan on 2009-05-13
Because /var/www is (by default) owned by root, you'll need to "sudo" in your files, change permissions on /var/www (not usually recommended) or move the DocumentRoot to a more accessible place.
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a good help page for some of those details.

---

### Post by bodhi.zazen on 2009-05-13
More specifically, [https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

That section will walk you through setting up a virtual host to use ~/html

See also : [HTTPD - Apache2 Web Server]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html")

---

### Post by philcamlin on 2009-05-14
thanks man i got it

---

