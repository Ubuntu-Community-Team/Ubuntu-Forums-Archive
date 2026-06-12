---
title: "Apache2 with SSL on startup"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by cowguru2000 on 2009-11-14
Hi guys,

What I want to do is have my Apache2 server start on computer startup. apache2 is already in /etc/init.d/ and has been working fine...

However, I recently installed a secure (SSL) site, so when I start up my computer, apache2 won't start (because the password for the SSL site is not provided). Of course, when I excecute sudo ```
/etc/init.d/apache2 start
``` it runs through and when I give it the password to the private key file, Apache starts up just fine.

However, I don't really feel like doing this every single time my computer starts up. How do I have the startup script somehow automatically have my computer provide the password so I don't have to manually start up every time?

-Joe

---

### Post by kita on 2009-11-15
I had a similar problem with something else. My solution was to go to /etc/sudoers file:

and add something like  this:

```
%username ALL= NOPASSWD: /pathtoApache2
```where the username is of sudo capability

you can then test to see if it works by;

```
sudo -K

sudo /etc/init.d/apache2 start
```


hope it works for you too!!

---

