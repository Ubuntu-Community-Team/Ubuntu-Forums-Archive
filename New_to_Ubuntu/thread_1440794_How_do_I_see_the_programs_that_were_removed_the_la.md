---
title: "How do I see the programs that were removed the last time I did &quot;apt-get autoremove&quot;?"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by hanzj on 2010-03-27
Hello,

How do I see the programs that were removed the last time I did "apt-get autoremove" (2 minutes ago).
I would like to do this auto-remove command.


When I installed something via apt-get, I got a message saying that programs X, Y, and Z were no longer needed and that I can remove them via apt-get autoremove.

Well, now my freemind doesn't work. Please help.

---

### Post by cosine352 on 2010-03-27
[http://www.debian-administration.org/articles/134](http://www.debian-administration.org/articles/134)

---

### Post by hanzj on 2010-03-28
i went to that page, but don't see the answer to my question.

---

### Post by cosine352 on 2010-03-28
I did not understand your problem. 

check the log file to see the changes. 
> gnome-system-log
and look for the > dpkg.log you should find them there.


Did you tried to reinstall it? 
> sudo apt-get reinstall freemind
or install it again
> sudo apt-get install freemind

---

### Post by hanzj on 2010-03-28
no i did not. because my freemind is not from apt-get.

BTW, freemind was not part of the group of programs that was auto-removed. but some java stuff that freemind needs to run were.

---

### Post by cosine352 on 2010-03-28
check the log file to see the changes.

> gnome-system-log
and look for the

> dpkg.log
you should find them there.

---

### Post by hanzj on 2010-03-28
thanks. found it.


I did 
> sudo apt-get install sun-java6-jre
and it installed these 2 as well


>  java-common sun-java6-bin


now freemind 0.9 rc 7 works again. thanks.

---

