---
title: "Troubling finding a file on my server."
date: 2009-08-03
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2009-08-03
I just got a server and a domain and I'm trying to install Wordpress.  However I can't seem to find my install.php file.  I mean, I can see it in Filezilla and such, but I haven't the foggiest where it actually is, because apparently, if I type in the directory into Firefox, nothing exists.

I actually don't even know what I'm doing.  I don't know where I'm supposed to upload the Wordpress directory or anything.  The documentation they give you is great for setting up your config files (and I've done that) but I have no clue how to actually install Wordpress.

Sorry for the stupid question.

---

### Post by wojox on 2009-08-03
Try:
```
locate install.php
```
or
```
whereis install.php
```
Upload wordpress to /var/www/

---

### Post by credobyte on 2009-08-03
Actually, you don't need to open install.php ! Once you upload your files to the server and open your domain ( eg. main directory ), you'll be prompted to enter blog information and admin stuff.

If you need to find a file and you've no idea where it could be, use:
```
find / -name "install.php"
```

---

### Post by bodhi.zazen on 2009-08-03
How are you installing wordpress ? did you install apache ? If so, you should get the famous "it works" when you browse to your server.

You then put your wordpress files into /var/www

How are you uploading the files ? is ftp chroot to your ~home ?

---

### Post by InfectedWithDrew on 2009-08-05
Never mind.  Figured it out myself.

Sorry for the trouble.

---

