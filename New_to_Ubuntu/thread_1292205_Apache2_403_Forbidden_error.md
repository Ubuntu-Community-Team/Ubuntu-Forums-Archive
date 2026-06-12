---
title: "Apache2 403 Forbidden error"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by adrenalin6 on 2009-10-15
Hello, im new to this forum and Im new to ubuntu, recently I been trying to make a server with apache and when ever I try to access it it gives me this. 

```
**Forbidden**

 You don't have permission to access /index.html on this server.
  Apache/2.2.11 (Ubuntu) mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80


```I tried everything, there is nothing in the error log. Any help would be greatly appreciated.

By the way, I got ubuntu 9.04

- Henry

---

### Post by zkriesse on 2009-10-15
Take a look at this...it's a page I wrote for this very thing as you pretty much won't find anything elsewhere. Keep in mind it's not yet finished but it should help you out if not just a little. Send me a message or an email from here and let me know the results.

---

### Post by adrenalin6 on 2009-10-15
> **Zachk18 said:**
> Take a look at this...it's a page I wrote for this very thing as you pretty much won't find anything elsewhere. Keep in mind it's not yet finished but it should help you out if not just a little. Send me a message or an email from here and let me know the results.
 Where can I find this?

---

### Post by sandyd on 2009-10-15
> **adrenalin6 said:**
> Hello, im new to this forum and Im new to ubuntu, recently I been trying to make a server with apache and when ever I try to access it it gives me this. 

```
**Forbidden**

 You don't have permission to access /index.html on this server.
  Apache/2.2.11 (Ubuntu) mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80


```I tried everything, there is nothing in the error log. Any help would be greatly appreciated.

By the way, I got ubuntu 9.04

- Henry
did you set the .htaccess and the folder permissions correctly.
and is there an index.html in the server directory (by default, /var/www)

---

### Post by adrenalin6 on 2009-10-15
> **carlee said:**
> did you set the .htaccess and the folder permissions correctly.
and is there an index.html in the server directory (by default, /var/www)

I did not set the .htaccess file, and yes there is a index.html file if your read the code I posted. mine is not  /var/www, its /home/(username)/www.

Where can I find this .htaccess?

---

### Post by diesch on 2009-10-15
What are the permissions for /home/username and /home/username/www?

---

### Post by zkriesse on 2009-10-15
> **adrenalin6 said:**
> Where can I find this?
Sorry 'bout that, here's the link. [https://help.ubuntu.com/community/UbuntuWithFirebirdDatabase](https://help.ubuntu.com/community/UbuntuWithFirebirdDatabase)

---

### Post by sandyd on 2009-10-15
can you do
```

sudo chown username ~/www
sudo chmod 777 ~/www
```if that works, its a folder permission issue.

and can you do
```

cat /etc/apache2/apache2.conf

```

and
```

dir /etc/apache2/sites-enabled/
cat /etc/apache2/sites-enabled/*

```

---

### Post by diesch on 2009-10-15
Making the folder writeable isn't needed, ~/ and ~/www just have to be executable for either www-data or all users.

---

### Post by adrenalin6 on 2009-10-15
> **carlee said:**
> can you do
```

sudo chown username ~/www
sudo chmod 777 ~/www
```if that works, its a folder permission issue.

and can you do
```

cat /etc/apache2/apache2.conf

```and
```

dir /etc/apache2/sites-enabled/
cat /etc/apache2/sites-enabled/*

```

Already did that, didnt work

---

### Post by adrenalin6 on 2009-10-15
> **diesch said:**
> What are the permissions for /home/username and /home/username/www?

How do you check permissions?

---

### Post by diesch on 2009-10-15
```
ls -ld /home/username  /home/username/www
```

---

### Post by adrenalin6 on 2009-10-15
> **diesch said:**
> ```
ls -ld /home/username  /home/username/www
```
For first I got 
```
drwxr-xr-x 45 adrenalin6 adrenalin6 4096 2009-10-15 15:24 /home/adrenalin6
```

and  for second I get ```

drwxrwxrwx 4 adrenalin6 adrenalin6 4096 2009-10-15 15:17 /home/adrenalin6/www

```

---

### Post by adrenalin6 on 2009-10-16
K, I figured everything out

---

### Post by ponchorage on 2009-11-06
How did you fix it? I'm having the same problem.

---

### Post by phunkizm on 2010-01-22
> **adrenalin6 said:**
> K, I figured everything out

:-x

It would be nice if you could tell us what you have figured out.  It is very frustrating to read through a thread to the end, only to find that it has been solved without an explanation.

---

### Post by mechanizedmedic on 2010-02-02
> **phunkizm said:**
> :-x

It would be nice if you could tell us what you have figured out.  It is very frustrating to read through a thread to the end, only to find that it has been solved without an explanation.

 i had the same issues with this and it ended up being the permissions. i found that the following info was what i needed to fix the problem.

   sudo chmod -R 755 /home/username/www 

 [http://ubuntuforums.org/showpost.php?p=1590980&postcount=2](http://ubuntuforums.org/showpost.php?p=1590980&postcount=2)

 ...why am i having to format my post with html?

---

