---
title: "Can´t view PHP files in browser"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by G!zZm0 on 2008-12-28
I want to learn PHP, so I downloaded LAMPP, but when I create a PHP file and double-click on it, it opens the text editor and I can´t view it on a browser...Can anyone help me fix this please????

---

### Post by willrowland on 2008-12-28
To view PHP files in a browser, you must have a IIS (on windows platforms) or Apache for either platform which can be downloaded from [http://httpd.apache.org/](http://httpd.apache.org/)  

> **G!zZm0 said:**
> I want to learn PHP, so I downloaded LAMPP, but when I create a PHP file and double-click on it, it opens the text editor and I can´t view it on a browser...Can anyone help me fix this please????

---

### Post by scott_g on 2008-12-28
To parse the php, your file must be in your web directory.  Assuming the default location, this is /var/www.  So, you would move your .php file to /var/www and go to [http://localhost/filename.php](http://localhost/filename.php) in your browser.

How did you install LAMPP?  I usually find it easiest to install the phpmyadmin package from synaptic, as it will install all the needed dependencies.

Scott

---

### Post by namdung on 2008-12-28
> **G!zZm0 said:**
> I want to learn PHP, so I downloaded LAMPP, but when I create a PHP file and double-click on it, it opens the text editor and I can´t view it on a browser...Can anyone help me fix this please????

Ur LAMP configuration is not properly done. Follow the guide below:
[http://ubuntuforums.org/showthread.php?t=1018760](http://ubuntuforums.org/showthread.php?t=1018760)

---

### Post by bodhi.zazen on 2008-12-29
See this link as well :

[http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

---

### Post by zephyrcat on 2008-12-29
Another things to try that has gotten me before, if you think you installed everything correctly, try issuing this command to restart apache:

```
sudo /etc/init.d/apache2 restart
```

---

