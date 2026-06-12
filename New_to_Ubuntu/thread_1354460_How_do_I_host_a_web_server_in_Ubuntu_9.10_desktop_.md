---
title: "How do I host a web server in Ubuntu 9.10 desktop edition?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by haveguitarwilltravel on 2009-12-13
Hello Ubuntu community, I need some help, I have a machine decent enough to host a web server on, but I don't want to host it on the server edition of ubuntu because that black screen gives me a headache.:D
So I was wondering if there is a relatively simple tutorial, or difficult tutorial with detailed instructions on how to host a web server on the desktop edition of Ubuntu 9.10 because I <3 GUI. If anyone could post a tutorial on how to do this, or provide me a link to one I would greatly appreciate it.

Also, if there was one right in front of me and I'm not looking hard enough to find it I apologize, I'm a lazy person.;)

---

### Post by spiderbatdad on 2009-12-13
[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

---

### Post by baddog144 on 2009-12-13
You can use something like apache or lighttpd (which I prefer). Google will give you plenty of info on setting either of these up :)

---

### Post by wenren on 2009-12-13
This really depends on what you are looking for in a server. However, if you don't have many configuration preferences, don't want to build from source, and only need mysql and php, I find that the easiest solution is to install a lamp server:

```
sudo tasksel install lamp-server
```

Then, add your website to /var/www/

---

