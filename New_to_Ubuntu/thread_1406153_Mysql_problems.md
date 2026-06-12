---
title: "Mysql problems"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by carrarin on 2010-02-13
Hello again,

I am having trouble setting up my msql. I installed the client and server mysqls. When I enter mysql into the command line I get the following results>


ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


Anyhelp would be greatly appreciated. 

Thanks

---

### Post by Shpongle on 2010-02-13
do you have the server running before you try to connect ?. im not familiar with mysql. in college most of our database stuff is for windows :rolleyes:, did you check the man pages ? , try man mysql

---

### Post by carrarin on 2010-02-13
I am not actually sure if there are other databases. I have checked the man pages, and I still can't figure out an answer.

---

### Post by Shpongle on 2010-02-13
there are other databases , oracle and access are examples of some.

have you tried any of these ? [http://www.google.com/search?q=ERROR+2002+(HY000):+Can't+connect+to+local+MySQL+server+through+socket+'/var/run/mysqld/mysqld.sock'&ie=utf-8&oe=utf-8&aq=t](http://www.google.com/search?q=ERROR+2002+(HY000):+Can't+connect+to+local+MySQL+server+through+socket+'/var/run/mysqld/mysqld.sock'&ie=utf-8&oe=utf-8&aq=t)

---

### Post by carrarin on 2010-02-13
I have looked on the internet for a solution, and can't find one. 

I find it interesting that mysql is trying to use a socket in the /var/run/mysqld/ folder. When I looked in there I didn'y find the mysqld.sock file.

Hmm?

---

### Post by Shpongle on 2010-02-13
> **carrarin said:**
> I have looked on the internet for a solution, and can't find one. 

I find it interesting that mysql is trying to use a socket in the /var/run/mysqld/ folder. When I looked in there I didn'y find the mysqld.sock file.

Hmm?

the database needs a server and in this case the server runs on your machine locally  , on a local socket (ip adress and port number) in most its 127.0.0.1:8080 i think 


what happens when you try this 'sudo /etc/init.d/mysql start' , post the output ,

---

### Post by carrarin on 2010-02-13
joseph@netbook:~$ sudo /etc/init.d/mysql start
[sudo] password for joseph: 
 * Starting MySQL database server mysqld                                 [fail]

---

### Post by Shpongle on 2010-02-13
> **carrarin said:**
> joseph@netbook:~$ sudo /etc/init.d/mysql start
[sudo] password for joseph: 
 * Starting MySQL database server mysqld                                 [fail]

did you configure it to use a port and ip address on the installation? 

you could try here [http://ubuntuforums.org/showthread.php?t=143492](http://ubuntuforums.org/showthread.php?t=143492)

---

### Post by carrarin on 2010-02-13
Hey, where is the mysql configuration file. I remember changing the user from root to me. 

I don't think it will sove my problems but we shall see.

---

### Post by Shpongle on 2010-02-13
im not sure , maybe /etc/mysql 

try asking your question at linux questions too , lots of experienced users there

[http://www.linuxquestions.org/](http://www.linuxquestions.org/)

sorry i cant be more help

---

### Post by carrarin on 2010-02-13
Nope, no change

---

### Post by Girya on 2010-02-13
your mysql server isn't running. start it by typing 
```
 sudo /etc/init.d/mysql start
```

in a terminal or try rebooting.

---

### Post by carrarin on 2010-02-13
I give up. Ill talk to my prof. 

Thnbaks anyways :=)

---

### Post by Shpongle on 2010-02-13
> **carrarin said:**
> I give up. Ill talk to my prof. 

Thnbaks anyways :=)
before you do try [http://www.linuxquestions.org/](http://www.linuxquestions.org/)

---

