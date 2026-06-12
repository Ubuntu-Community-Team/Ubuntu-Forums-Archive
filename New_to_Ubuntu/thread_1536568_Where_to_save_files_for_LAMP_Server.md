---
title: "Where to save files for LAMP Server"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by jkries on 2010-07-22
I just installed LAMP under a brand new Ubuntu 10.04 installation.

It looks as though the files I wish to serve are located here: /var/www

But when I try to save new files into that folder, I am told I don't have permission.

Please advise.  My only experience is with WAMP under Windows and I never had problems saving to the server folder there.

---

### Post by mcduck on 2010-07-22
You are correct, the default root directory is /var/www. And what comes to permissions, that's like it should be; normal user's only have write access to their own home directories while all the system directories are for root user only.

Just run "gksudo nautilus" to open the file manager as root, that will allow you to move your files into /var/www.

..and be sure to read this document about how admin privileges are handled in Ubuntu: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Of course you can configure the web site root to be anywhere you want it, or enable the user www directories. Or if it's a development server and not actual production server you could simply create a WWW directory in your home and then link it into /var/www for easier access without requiring root privileges when adding/modifying things in your web site.

Here's a good guide how to use & configure LAMP in Ubuntu: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by jkries on 2010-07-22
Do I need to set permissions on those folders somehow?

I get a 403 error when I access the pages off the server.

---

### Post by mcduck on 2010-07-22
Yes, directories should be 755 (rwxr-xr-x) and files 644 (rw-r--r--).

In other words httpd needs to have read and execute permission on directories and read permission on files. And since your files will most likely be owned either by root or you, and httpd doesn't belong to either one of these groups, it's the permissions for "others" that counts here.

---

