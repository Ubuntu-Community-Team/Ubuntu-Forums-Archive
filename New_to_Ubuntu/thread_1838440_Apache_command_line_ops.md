---
title: "Apache command line ops"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by jacknet52 on 2011-09-03
I&#7743; trying to do a tutorial in Matt Doyle&#347; book PHP 5.3 and ran the lamp-server to load the programs for studying the book. The first little test blew up saying I didn´t have permission to save the testing.html file to /var/www in the Apache Server root folder. I can´t find Apache in applications anywhere and don´t know enough about terminal command line procedures. Anyone have suggestions to learn Apache on linux or command line ops.

---

### Post by cariboo on 2011-09-04
Because you aren't the owner of /var/www, you have to be root to save the file. You can use sudo to copy the file to /var/www:

```
sudo cp testing.html /var/www/
```

to copy files to /var/www without using sudo, make yourself a member of the www-data group. You can add yourself to the group in System->Administration->Users & Groups.

---

