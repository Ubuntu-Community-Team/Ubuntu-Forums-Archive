---
title: "PHPMyadmin Troubles"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by KMC7500 on 2008-02-01
I have just installed PHPMyAdmin and am attempting to log into it however when I enter //localhost/phpmyadmin it asks to download a .phtml file.  I searched and found many references to this and the common way to fix it is to find/edit  
AddType application/x-httpd-php .php .php3 .phtml in my httpd.conf file.  When I do a gksudo gedit httpd.conf the file is empty...I added the line anyway but to no avail.  I also dont have a directory index in my apache2.conf file and maybe thats related?  The only thing I can think of is perhaps the prder I dl'ed and installed the programs but I did apache2 first and then mysql php5 all from the terminal with apt get install.  Any input would be appreciated.

---

### Post by ssuehr on 2008-02-01
You might try a 'grep -r httpd-php /etc/' to find out where the file is that's controlling the mime types.  That's where you'd probably need to add the handling for .phtml.

Steve

---

