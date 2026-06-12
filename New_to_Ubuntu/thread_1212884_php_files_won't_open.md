---
title: "php files won't open"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by benh13 on 2009-07-14
I am learning to write in php, and have created some test php files. however, when i try to open them via firefox, it sees them as a download, instead of showing it as an internet file. i have tried putting these php files in var/www and opening them, but it still won't work. the files are written in a combination of both php and html. i have tried saving the files as both .html and .php, but html comes up with a blank internet page, and .php comes up with a download type message, rather than opening it up on the internet.  does anybody know wht might be wrong?
thanks

---

### Post by Hospadar on 2009-07-14
Do you have mod_php installed in apache? (specifically the libapache2-mod-php5 package in synaptic)

Also I believe the php files need to be executable by the webserver ("www-data" group).  The easy thing to do is "chmod uog+x yourfile.php"

Read more on chmod, a2enmod (the apache module tool) and unix permissions if any of this doesn't make sense, google can help you out there.

---

### Post by wojox on 2009-07-14
In terminal:

```
sudo a2enmod php5
```

Then:

```
sudo /etc/init.d/apache2 restart
```

And clear your browser cache.

---

### Post by Tibuda on 2009-07-14
> **benh13 said:**
> I am learning to write in php, and have created some test php files. however, when i try to open them via firefox, it sees them as a download, instead of showing it as an internet file. i have tried putting these php files in var/www and opening them, but it still won't work. the files are written in a combination of both php and html. i have tried saving the files as both .html and .php, but html comes up with a blank internet page, and .php comes up with a download type message, rather than opening it up on the internet.  does anybody know wht might be wrong?
thanks
When you save them in /var/www, you have to open them in [http://localhost](http://localhost) , not /var/www. PHP is server-side, you should run it through a (local) server.


> **Hospadar said:**
> Also I believe the php files need to be executable by the webserver ("www-data" group).  The easy thing to do is "chmod uog+x yourfile.php"No, they don't need.

---

### Post by benh13 on 2009-07-14
thanks, the problem was i needed to open them via localhost lol

---

