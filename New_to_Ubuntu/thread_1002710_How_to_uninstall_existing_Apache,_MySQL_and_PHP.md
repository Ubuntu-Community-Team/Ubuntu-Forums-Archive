---
title: "How to uninstall existing Apache, MySQL and PHP"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by G!zZm0 on 2008-12-05
How can I uninstall an existing Apache, MySQL and PHP so that I can then install XAMPP. Because I had XAMPP installed and it gave me this output:

[I]Starting XAMPP for Linux 1.6.8a...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.[/I]



Thanks a lot!

---

### Post by jenkinbr on 2008-12-05
```
sudo apt-get remove apache2 mysql php5
``` should do it.

---

