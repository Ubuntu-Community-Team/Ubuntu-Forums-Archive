---
title: "logging in to phpmyadmin problem"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by zeroid on 2009-10-31
I am a complete novice at Linux systems. I have recently installed 9.04 desktop and added a LAMP server. All seems to be OK with the installation. Apache works, PHP works, MYSQL works. I am seeing the webpage in my browser for phpmyadmin. However I can't log into phpmyadmin. It doesn't recognise my password which I used during the LAMP installation and the phpmyadmin installation. I get "#1045 Access denied for user 'myname'@'localhost' (using password:YES)" and if I don't type in a password I get the same message but "NO" at the end. 

I've checked all the phpmyadmin forums and there seems to be a thousand different permutations of this problem. 

It's probably something really simple, but can anyone help a complete novice to figure this out? 

Many thanks

---

### Post by zeroid on 2009-10-31
Didn't get any reply from anyone, however, as suspected it was a ridiculously simple thing. The user name and password as set during LAMP install doesn't get automatically transferred to phpmyadmin. Had to log in as "root" for the user name and that did it. Sheesh. Oh well maybe my misfortune might save the next guy some time.

---

### Post by liquidbee on 2009-10-31
[Set / Change / Reset the MySQL root password on Ubuntu Linux]("http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/") - let us know if it helps.

---

