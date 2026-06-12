---
title: "Newbie file sharing question"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by enigma260671 on 2008-10-06
I have installed Apache and want to share the www folder so that I can write to it from a windows network.

I have installed SAMBA, but I can't figure out how to use it.  There is an option when you right-click a folder to configure sharing, but it won't work because it needs SUDO.  
Is there a way to run things as SUDO through the GUI?
If not, how do I configure a share that will work in windows?
Is there another way to get my web-sites onto my server?

---

### Post by superprash2003 on 2008-10-06
you might have made some mistake while configuring samba, hopefully this should help [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html) .. share the /var/www folder and uncheck "Read only"

---

### Post by Iowan on 2008-10-06
**/var/www** is owned by root (at least on my default LAMP install).  You may need to change the directory settings - or point your virtual host DocumentRoot elsewhere.  [This]("https://help.ubuntu.com/community/ApacheMySQLPHP") page helped me get started.

---

