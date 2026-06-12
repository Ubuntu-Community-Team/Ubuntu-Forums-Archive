---
title: "Help With Apache and Displaying PHP Page"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by pkjm17 on 2010-09-17
I renamed my var/www/index.html page index.php. And now when I try to open it to view it as a web page it will only open up the source code in gedit. Firefox won't open it. How do I get Firefox to display my var/www/index.php page?

Thanks

---

### Post by JustinR on 2010-09-17
Make sure your have PHP for Apache installed:

```

sudo apt-get install libapache2-mod-php5

```

Reboot your computer and try it out.

---

### Post by vivek40 on 2010-09-18
Please post the link you are using in the browser.. you are supposed to use something like this below:-
[http://localhost/index.php](http://localhost/index.php)
and not the directory structure which I guess you might be using!

---

### Post by pkjm17 on 2010-09-18
> **vivek40 said:**
> Please post the link you are using in the browser.. you are supposed to use something like this below:-
[http://localhost/index.php](http://localhost/index.php)
and not the directory structure which I guess you might be using!

Oh ok thanks! I was using the var/www/index.php in the browser. I didn't know you can't use it. But it will display /var/www/index.html in the broswer.

Anyway [http://localhost/index.php](http://localhost/index.php) works and so does [http://127.0.1.1/](http://127.0.1.1/)

Thanks again!

---

### Post by vivek40 on 2010-09-18
Please mark it as solved!

---

### Post by CharlesA on 2010-09-18
> **vivek40 said:**
> Please mark it as solved!
Done. :)

---

