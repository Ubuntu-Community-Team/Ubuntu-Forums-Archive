---
title: "Help installing mysql 5.1.40 on my ubuntu plz"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by killerblack on 2009-11-15
Hi there "i use ubuntu 9.10 x64bit" and
I,m reading the book called "build ur own database drive web site with php and mysql 4th edition"
trying to install mysql database manually on my ubuntu system and here is what happens.

I downloaded mysql 5.1.40 and extracted it due to the guide in the book
I made a shortcut to it named "mysql" as written also
,added group and user to use  mysql like in the book

[php]root@machine:/usr/local/mysql# groupadd mysql 
root@machine:/usr/local/mysql# useradd -g mysql mysql 
root@machine:/usr/local/mysql# chown -R mysql . 
root@machine:/usr/local/mysql# chgrp -R mysql .  [/php]Then i have gone to mysql directory and tried to continue following the book instructions:
[php] root@machine:/usr/local/mysql# scripts/mysql_install_db --user=mysql  [/php]and here is my own terminal code for this last step:
[php]root@killer-desktop:/usr/local/mysql# scripts/mysql_install_db --user=mysql 

FATAL ERROR: Could not find mysqld 

The following directories were searched: 

    /usr/libexec 
    /usr/sbin 
    /usr/bin 

If you compiled from source, you need to run 'make install' to 
copy the software into the correct location ready for operation. 

If you are using a binary release, you must either be at the top 
level of the extracted archive, or pass the --basedir option 
pointing to that location. 

root@killer-desktop:/usr/local/mysql#[/php]And i dont know what to do plz help me solve this problem i,m very new ubuntu user btw,
 so plz try to  give me details as much as u can 
and thanks in advance for ur help guyz.

i wish there is someone there have this book so it can be easier to help me its from sitepoint.com

and i will try to put all the code from the book that guides me for installation now so this may help u more in fixing my problem.

[php]user@machine:~$ sudo su
root@machine:/home/user# cd /usr/local
root@machine:/usr/local# tar xfz ~user/Desktop/mysql-version-linux-
&#10149;platform.tar.gz
root@mythril:/usr/local# tar xfz ~kyank/Desktop/mysql-5.1.34-linux-x
&#10149;86_64-glibc23.tar.gz
 oot@machine:/usr/local# ln -s mysql-version-linux-platform mysql
root@machine:/usr/local# cd mysql
root@machine:/usr/local/mysql# groupadd mysql
root@machine:/usr/local/mysql# useradd -g mysql mysql
root@machine:/usr/local/mysql# chown -R mysql .
root@machine:/usr/local/mysql# chgrp -R mysql .
root@machine:/usr/local/mysql# scripts/mysql_install_db --user=mysql
[/php]this is the last statement i wrote before seeing the error "i wish this is enough info for u to help me solve this"
thanks alot.

---

### Post by yeats on 2009-11-15
Is there a reason you need this particular version?  It would be easiest to install MySQL from the repositories (System -> Administration -> Synaptic Package Manager).  The functionality will be nearly identical.

---

### Post by killerblack on 2009-11-15
this paragraph is in thie book and should explain to u why i do it that way "the writer of the book wanna me do it like dat"

> These prepackaged versions of software are really easy  to install; 
unfortunately, they also limit the software configuration options available
to you. For this reason&#8212;and because any attempt to document the procedures for
installing the packaged versions across all popular Linux distributions would be
doomed to failure&#8212;I will instead show you how to install them manually.


---

### Post by yeats on 2009-11-15
> this paragraph is in thie book and should explain to u why i do it that way "the writer of the book wanna me do it like dat"

It's obviously your call, but I would just install from the repos and make do...  It is true that if you need specific options compiled into the program, then you would need to do it from source, but even then there are *many* options for those sorts of things in the repos as well.  Either way, good luck with your installation.

---

### Post by killerblack on 2009-11-15
anyone??

---

