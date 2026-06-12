---
title: "How do I work on PHP pages OFFLINE?"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by jhsu802701 on 2010-12-20
I'm working on web site that use PHP.  So far, I can only view the PHP pages online.  That means that every time I make a change, I have to upload the files involved and then view them.  I'd work so much more smoothly if I could see the results of my changes OFFLINE and not have to keep uploading files.  So how do I work on PHP pages offline?  I have php5 and apache2 installed.  I'm using antiX Linux (which is based on Debian-derived MEPIS).

---

### Post by charlie_b on 2010-12-20
Place your files in the localhost folder, which is /var/www. Ensure that apache and php daemons are started. Then you should be able to see your pages by navigating Firefox to the localhost folder.

---

### Post by jhsu802701 on 2010-12-20
> **charlie_b said:**
> Place your files in the localhost folder, which is /var/www. Ensure that apache and php daemons are started. Then you should be able to see your pages by navigating Firefox to the localhost folder.

I'm still unable to view my PHP pages.  How do I confirm that apache and php are working?

---

### Post by -LynX- on 2010-12-20
> **jhsu802701 said:**
> I'm working on web site that use PHP.  So far, I can only view the PHP pages online.  That means that every time I make a change, I have to upload the files involved and then view them.  I'd work so much more smoothly if I could see the results of my changes OFFLINE and not have to keep uploading files.  So how do I work on PHP pages offline?  I have php5 and apache2 installed.  I'm using antiX Linux (which is based on Debian-derived MEPIS).

I use [LAMPP]("http://www.apachefriends.org/en/xampp-linux.html") for this. Quite easy to install. ;)

---

### Post by stmiller on 2010-12-20
Enable php:

```
sudo a2enmod php5 
```

Restart apache:

```
sudo apache2 restart 
```

---

