---
title: "Apache Help [noob]"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by helloinsomnia on 2007-12-14
I have apache installed but im not sure what to do.  I found localhost but I can't put php scripts in /var/www it wont let me..  Any ideas or suggestions would be grateful.

---

### Post by MossKiller on 2007-12-14
You need to be root to create and write to files in /var/www. Either copy your scripts using 'sudo cp index.php /var/www/index.php' or you can run a nautilus window as root using 'gksudo nautilus /var/www', but make sure you don't leave that window open once you've copied the files.

---

### Post by helloinsomnia on 2007-12-15
Thank you, very helpful.

---

