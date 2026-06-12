---
title: "regarding apache web server"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by xardox69@gmail.com on 2009-07-21
hi,
guyz im new to lunix and im not getting the starters guide to installing apache on ubuntu...need help!!!!

---

### Post by saj0577 on 2009-07-21
Apache alone

```
sudo apt-get install apache2
```

But for a fully working server you may want a LAMP set up which gives you sql and PHP as well.


[https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202](https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202)


Need any more help just shout,if really stuck I can guide you through it step at a time.

Saj

---

### Post by credobyte on 2009-07-21
> **saj0577 said:**
> Apache alone

```
sudo apt-get install apache
```But for a fully working server you may want a LAMP set up which gives you sql and PHP as well.


[https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202](https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202)


Need any more help just shout,if really stuck I can guide you through it step at a time.

Saj

Just a quick note - he should install *apache2*, not *apache* :)

---

### Post by saj0577 on 2009-07-21
> **credobyte said:**
> Just a quick note - he should install *apache2*, not *apache* :)



Cheers my bad, forums dont have tab complete lol.

Saj

---

### Post by xardox69@gmail.com on 2009-07-21
used this command
apache2 php5-mysql libapache2-mod-php5 mysql-server
installed the lamp stack now what????
where is my local web site

---

### Post by xardox69@gmail.com on 2009-07-21
just want to see a web page like welcome user etc etc

---

### Post by credobyte on 2009-07-21
**Document root**: /var/www/
**URL:** [http://localhost/](http://localhost/)

---

### Post by saj0577 on 2009-07-21
website files stored in 
/var/www/

And if you navigate to
[http://localhost/](http://localhost/)

that will be your website. (It should say "It Works!")

Do you see this message?

Saj

---

### Post by xardox69@gmail.com on 2009-07-21
where is this path     /var/www/  ????? tell me from user@ubuntu

---

### Post by credobyte on 2009-07-21
> **xardox69@gmail.com said:**
> where is this path     /var/www/  ????? tell me from user@ubuntu

```
cd /var/www/ && ls -l
```

---

### Post by xardox69@gmail.com on 2009-07-22
why is this when im in root directory and use ls , it doesnt show var as directory but when i use cd /var , it goes into directory

---

### Post by xardox69@gmail.com on 2009-07-22
can anybody tell me wht is difference between cd /var and cd var

---

### Post by Durden on 2009-07-22
"/var" is a complete path "/" is the top level directory, like "C:\" is in windows. Doing "cd var" would assume there is a "var" directory inside the one you are in now, doing a "cd /var" takes you to the var inside the "/" directory.

I think you should read some documentation on how the unix filesystem works.

---

### Post by cpetercarter on 2009-07-22
The initial forward slash / means the root directory.
So "cd /var" means "move me to the var directory at the next level down from the root".
"cd var" just means "move me to the var directory which is at the next level down from where I am at the moment". So if you are in, say the /etc directory, "cd var" would move you to /etc/var - except it wouldn't because (probably) /etc/var does not exist in your system.

---

