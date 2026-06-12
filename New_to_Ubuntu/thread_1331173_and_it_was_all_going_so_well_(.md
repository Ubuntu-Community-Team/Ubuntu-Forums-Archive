---
title: "and it was all going so well :("
date: 2009-11-19
forum: New to Ubuntu
---

### Post by h20boynz on 2009-11-19
ok so I was getting things in order...had remote access using ssh/putty up and running...all is well with the world. Thought I might have a go at setting up FTP transfers using Vsftpd.
Installed it and set some port forwarding etc.  Also installed Nessus...kind of..had some trouble with that one..any ways now I've lost access to my Webmin and putty and when I try to view the index.html file under /var/www it is asking for a login and password.
It didn't do this before and I have no idea what i changed to make this happen????

---

### Post by ukripper on 2009-11-19
> **h20boynz said:**
> ok so I was getting things in order...had remote access using ssh/putty up and running...all is well with the world. Thought I might have a go at setting up FTP transfers using Vsftpd.
Installed it and set some port forwarding etc.  Also installed Nessus...kind of..had some trouble with that one..any ways now I've lost access to my Webmin and putty and when I try to view the index.html file under /var/www it is asking for a login and password.
It didn't do this before and I have no idea what i changed to make this happen????

you must have enabled Basic authentication or Digest authentication on your website. 

Did you do something like this : a2enmod auth_digest ? 

Check your /etc/apache2/sites-available/**and-your-websites-there**

---

### Post by halovivek on 2009-11-19
Hi 
could you please give some more additional information?
system configuration, current linux version, HDD, RAM
so it will help us to solve.

---

### Post by h20boynz on 2009-11-19
> **ukripper said:**
> you must have enabled Basic authentication or Digest authentication on your website. 

Did you do something like this : a2enmod auth_digest ? 

Check your /etc/apache2/sites-available/**and-your-websites-there**

Ah ha!...yeah i remember something like this during the setup for one of the programs i installed.
What is the correct setting for a2enmod?

Not sure where to look for this.

I looked under /sites-available/ and there are two files: default and default-ssl which contain <virtual host:80> and <virtual host:443> settings.  I can post these if it helps???

I have ubuntu 9.10 server installed, 2.8ghz P4, 40gb HDD, 512mb ram.

---

### Post by ukripper on 2009-11-19
> **h20boynz said:**
> Ah ha!...yeah i remember something like this during the setup for one of the programs i installed.
What is the correct setting for a2enmod?

Not sure where to look for this.

I looked under /sites-available/ and there are two files: default and default-ssl which contain <virtual host:80> and <virtual host:443> settings.  I can post these if it helps???

I have ubuntu 9.10 server installed, 2.8ghz P4, 40gb HDD, 512mb ram.

yes post them here.

---

