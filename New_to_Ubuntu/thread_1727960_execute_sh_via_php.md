---
title: "execute sh via php"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by Jebajseti on 2011-04-13
Hi,

i have dedicated server and i have buyed hosting,
i would like to add on my site a php file that executes .sh file on dedicated server

i'm beginner in this, know some stuff but i would need an example of that

anyway lets say i have user named Jebajseti with password mypassword and i want to execute /home/jebajseti/startserver.sh via web remote site

like something this
[B]ssh connect 255.255.255.255 Jebajseti@mypassword sh /home/jebajseti/startserver.sh

[/B]i have been searching over this forum google and didnt find nothing that would help me

Regards

---

### Post by stoogiebuncho on 2011-04-13
You can learn about PHP and command-line scripting here:
[http://www.tuxradar.com/practicalphp/21/2/0]("http://www.tuxradar.com/practicalphp/21/2/0")

---

### Post by SeijiSensei on 2011-04-13
Just remember that the PHP user will have the same username and privileges as the user running apache.  For instance, apache2 on Ubuntu runs as the user "www-data" so a PHP script will also run as the www-data user.  On RedHat/CentOS machines, this user is called "httpd".

---

### Post by Jebajseti on 2011-04-13
well i finnaly got it working :) found some tutorial just by accident^^

so i have one question more, since i'm starting server i would like to make some .sh file that does following

screen -r
type into console: g_password "myserver"
and triggers deatach ctrl + a d

Thanks forward for replies

---

