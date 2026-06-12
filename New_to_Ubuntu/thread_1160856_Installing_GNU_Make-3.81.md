---
title: "Installing GNU Make-3.81"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by fugufish95 on 2009-05-16
Hi, so after following the INSTALL instructions to the letter, I type "./configure", and it runs fine. Typing "make" also works just as it should. But when i enter "make install", i get this: 
(after normal make files and stuff like that)
...installing ga.gmo as /usr/local/share/locale/ga/LC_MESSAGES/make.mo
mkdir -p -- /usr/local/share/locale/gl/LC_MESSAGES
mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/gl/LC_MESSAGES/make.mo': No such file or directory
installing gl.gmo as /usr/local/share/locale/gl/LC_MESSAGES/make.mo
mkdir -p -- /usr/local/share/locale/he/LC_MESSAGES
mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/he/LC_MESSAGES/make.mo': No such file or directory.......... and it repeats about 10 times. @ the end it says error 1 and error 2 What am I doing wrong and how can I fix it? 
--->SYSTEMINFO<---           Ubuntu 9.04 on Dell Inspiron 1420/Dual Boot Vista Home Premium

---

### Post by coffeeaddict22 on 2009-05-16
Permission denied is not uncommon.  The short answer:  ```
sudo make install
```
The longer answer:  I guess you're aware Ubuntu does security a little differently to some more common systems.  Essentially, you work in "userspace"; to modify anything that messes with the system itself, you have to explicitly allow it by becoming a "root user" or "superuser".  Ubuntu is designed for people unfamiliar with Linux, so you can't log in as a root user or super user easily; instead, when you want a command run as superuser, you preface it with "sudo", and once the command is done you're dropped back into userspace.

---

### Post by fugufish95 on 2009-05-16
OK thanx :-) PS that actually makes sense!!

---

