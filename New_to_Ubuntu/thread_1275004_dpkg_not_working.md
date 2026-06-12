---
title: "dpkg not working"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by wobin77 on 2009-09-25
Hi,

When i try to use dpkg in terminal, it does nothing. 
For example i want to use the bytecode hinting:

```
wobin@wobin-desktop:~$ sudo dpkg-reconfigure fontconfig-config
[sudo] password for wobin: 
wobin@wobin-desktop:~$ 

```

and that's all that happens. Same for other dpkg commands. 

Am i missing something here? 


Thanks!

---

### Post by halitech on 2009-09-25
obvious question, are you putting in your password and are you a member of the sudo group?

---

### Post by NightwishFan on 2009-09-25
The command may not necessarily give back output. Bash does not say.. It worked! It only prints errors. (Generally, some programs print stuff anyway, such as apt-get.)

---

### Post by philinux on 2009-09-25
[https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/364632](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/364632)

---

### Post by wobin77 on 2009-09-28
Did the trick! Thanks!

---

