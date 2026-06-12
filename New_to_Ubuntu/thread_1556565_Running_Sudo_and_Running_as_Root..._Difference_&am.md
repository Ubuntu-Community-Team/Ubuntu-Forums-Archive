---
title: "Running Sudo and Running as Root... Difference? &amp; locale"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Jyotirmo Ry on 2010-08-19
Doesn't running sudo gives you root privilege ? Or by using sudo su you get root access? Explain please? :mad:

Why I'm not getting the same result here :

[
ami@ami-desktop:~$ locale
LANG=en_US.utf8
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

]

[

ami@ami-desktop:~$ sudo su
[sudo] password for ami: 
root@ami-desktop:/home/ami# locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

]


My first post here. Hope you guys can resolve :D

---

### Post by s.fox on 2010-08-19
Hello,


[This]("http://ubuntuforums.org/showpost.php?p=1349903&postcount=3") post from from [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941") should help clarify the difference between su and sudo.

> You can log in as a sudo user as many times as you want. The sudo user doesn't have administrative privileges unless she uses the command sudo or gksudo or kdesu--which is authenticated with a password. Otherwise, she's a user just like any other user.

-Silver Fox

---

