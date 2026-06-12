---
title: "----&gt;drupal on ubuntu.. lord i hope some knows howto..."
date: 2009-09-13
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-13
could some one give me some (easy, ya i knowright?) instructions on installing drupal on my ubuntu studio 9.04? also some good write ups on how to use drupal would be nice as well... i have to build a web sight for my class no one else was willing to put there neck out to do it..
Thanks!

---

### Post by ainsworth_t on 2009-09-13
Try this howto from the Ubuntu Community Documentation: [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

---

### Post by R3fr4cti0n on 2009-09-13
ya i found that one but i dont understand it could someone explain?

---

### Post by R3fr4cti0n on 2009-09-13
found it out!

In the last year the Drupal package was not in Debian/Ubuntu, now it is back. So after a fresh install of Jaunty, just type:

```
sudo apt-get install drupal6
``` and then you have to restart the webserver:

```
sudo /etc/init.d/apache2 restart
``` And you will see the Drupal install pages here:

```
http://localhost/drupal6/install.php
 

```

---

### Post by R3fr4cti0n on 2009-09-15
now how do uninstall it?

---

### Post by go2dell on 2009-09-18
```
sudo apt-get remove drupal6
``` or ```
sudo apt-get remove drupal5
``` will remove Drupal and all the related dependencies you installed, depending on which version you installed.

If you want the latest versions of Drupal, including all security bugfixes, please feel free to test out my [PPA]("https://launchpad.net/~scott-testerman/+archive/ppa").

---

