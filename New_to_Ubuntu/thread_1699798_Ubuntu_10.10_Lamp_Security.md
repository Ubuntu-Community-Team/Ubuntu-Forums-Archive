---
title: "Ubuntu 10.10 Lamp Security"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by abujp1993 on 2011-03-04
HI, I have Ubuntu 10.10 & Working Installed Lamp (Everyone Helped me to fix my problems on another thread):)

My next question is I want to protect it from hackers or secure my Web server and i don't have any experience on security so if some one shows me the steps or any website it would be great.

Thanks in advance:)

---

### Post by aeiah on 2011-03-04
its fairly secure out of the box as far as i know, but common pitfalls are:

[LIST]
[*]opening mysql to the outside world
[*]having insecure php code that enables sql injection
[*]having a weak ssh password (if you have physical access to the box, you may consider turning password authentication off all together and only using passkeys. if the server is remote this could bite you in the *** if you lose your private key though)
[*]not patching known security vulnerabilities (ie, keep it up to date)
[/LIST]

---

### Post by abujp1993 on 2011-03-04
Thanks for your fast reply but im not using mysql bcuz i really dont understand what is it actually. (I know that mysql is database. ) & i'm not using php also i dont know what is it but in future i like to study it.
If its necessary to learn PHP & MYSQL Please tell ill learn it as fast as I can

So you mean if I don't use mysql my pc is secured a little bit more?:confused:

---

### Post by coffee412 on 2011-03-04
> **abujp1993 said:**
> Thanks for your fast reply but im not using mysql bcuz i really dont understand what is it actually. (I know that mysql is database. ) & i'm not using php also i dont know what is it but in future i like to study it.
If its necessary to learn PHP & MYSQL Please tell ill learn it as fast as I can

So you mean if I don't use mysql my pc is secured a little bit more?:confused:

Install mod_security. There is a lot of reading you can find on it. I have it running but Im running a fedora box with it. 

Mysql ---> Mysql is of course a database program. What a database program basically is -- A program that stores alot of information that can be retrieved quickly. Running mysql is easy and learning the basics is not hard at all. 

Alot of programs use a database program to store information like usernames, passwords, and other values. If your ever thinking of running a message board or some other website features you will find something like mysql very handy (and required) to keep track of information on the website.

I get most of my questions answered not by asking but by googling.

For instance:

google ---> Ubuntu install mod_security.

Have fun!

coffee:)

---

### Post by abujp1993 on 2011-03-04
Thankyou!! know I got the actual mean of MySQL(Type of Databae) & Try To learn after installing the mod_security & fedora box.:D

ok i'll try more googling:lolflag:
I'll reply the results.

---

### Post by dragon999 on 2011-03-04
As aeiah said: keep your os up to date! This will help to secure your system! Run your update manager often. I try to do it first thing when I boot in. Also, make sure you have a strong password, I change mine every few months, just to make sure.

I found this link, I hope it will help a little.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by abujp1993 on 2011-03-04
Thanks for fast reply & a nice advice!!!:KS

---

### Post by coffee412 on 2011-03-04
> Thankyou!! know I got the actual mean of MySQL(Type of Databae) & Try To learn after installing the mod_security & fedora box.:D

Dont get me wrong though. Im not saying "switch to fedora". What Im just saying is that my fileserver/router/ssh/webserver box runs fedora so some things are different. If you have ubuntu server installed and running stick with that and install mod_security. From what I have read so far is that there is more config to do with ubuntu install of M_S than fedora. But fedora is cutting edge and updates every 6 months. They only support about 3 versions and it drops off. If you want LTS then stick with Ubuntu or try CentOS. 

GOOD LUCK and have FUN!

coffee

---

### Post by abujp1993 on 2011-03-04
:lolflag:I thought Fedora is security soft sorry i miss understand.
I will install Mod Security & reply the results:P
& I looooove Ubuntu:KS
Thx again!!

---

### Post by maeyukii on 2012-12-23
how to run lamp in my netbook?

---

### Post by Wim Sturkenboom on 2012-12-23
I'm sure that this thread will be closed shortly because it's old.

To install:
```

sudo apt-get install lamp-server^

```
Don't forget the '^' at the end.

To run: it should be running after installation.

---

