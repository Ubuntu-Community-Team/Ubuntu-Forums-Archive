---
title: "Avast problem?"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by Old-un on 2011-06-26
I am running Lubuntu 11.04 and have downloaded Avast anti-virus and everything appeared to be ok until i went to: Main menu -> Accessories -> avast Antivirus and was then informed that an error had occurred.

An error occured in avast! engine: Invalid argument

I did do a search via Google which said to open a terminal and type the following command:
sudo syscti -w kernel.shmmax=128000000

The output of the above command was:
sudo: syscti: command not found

I have been told quite a few times that i don't need an anti-virus but i do have a lot of contact with user's who have not as yet seen the light and start using Linux so i really would appreciate any help or advice.

---

### Post by yetiman64 on 2011-06-26
[http://ubuntuforums.org/showpost.php?p=9512526&postcount=9](http://ubuntuforums.org/showpost.php?p=9512526&postcount=9)

The above is a post I did a while back for the Avast database and the Ubuntu kernel shmmax value fix. Change the value I posted in the above post to 128000000 I used 100000000 back then. It should help you out. Good luck.

Regards from yetiman64.

Edit: the reason the code you listed above failed is the command is sysctl (that's a lower case L on the end) not syscti.

---

### Post by Old-un on 2011-06-26
Really big thanks yetiman64. Cheers mate!

---

### Post by checoimg on 2011-07-06
GREAT! Very NICE! :D I can't imagine how do you know this solution I will be reading your post for more info yetiman64. And thank you Oldrun for ponsting here.  Keep Ubuntuing!

---

### Post by createdcreature on 2011-07-06
You don't need and anti virus on Linux.;)

---

### Post by Elfy on 2011-07-06
> **Robert Moyse said:**
> You don't need and anti virus on Linux.;)

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

You might not - other people might.

---

### Post by checoimg on 2011-07-06
LOL! I'm so tired that in every post about avast inside Linux someone appears to say that Robert. Be realistic you don't know everything and most of all he is asking for help to install it not to know if he needs it. I really would like to know if there is a better Opensource solution like Avast. Clamav? does it has a better virus database?

---

### Post by EngineersGarage on 2011-12-03
ii tried this... it doesnt work for me...:(

will@will-desktop-ubuntu:~$ sudo syscti -w kernel.shmmax=128000000
[sudo] password for will: 
sudo: syscti: command not found
will@will-desktop-ubuntu:~$ sudo syscti -w kernel.shmmax=128000000
sudo: syscti: command not found
will@will-desktop-ubuntu:~$ sudo syscti -w kernel.shmmax=100000000
sudo: syscti: command not found
will@will-desktop-ubuntu:~$ sudo syscti -w kernel.shmmax=128000000
sudo: syscti: command not found

---

### Post by westie457 on 2011-12-03
> **EngineersGarage said:**
> ii tried this... it doesnt work for me...:(

will@will-desktop-ubuntu:~$ sudo syscti -w kernel.shmmax=128000000
[sudo] password for will: 
sudo: syscti: command not found
will@will-desktop-ubuntu:~$ sudo syscti -w kernel.shmmax=128000000
sudo: syscti: command not found
will@will-desktop-ubuntu:~$ sudo syscti -w kernel.shmmax=100000000
sudo: syscti: command not found
will@will-desktop-ubuntu:~$ sudo syscti -w kernel.shmmax=128000000
sudo: syscti: command not found

If you read 'yetiman64's EDIT it will explain why this failed.

---

### Post by EngineersGarage on 2011-12-03
Aw Thanx Man...missed that one!:P

It works again after fix! Shot!

---

