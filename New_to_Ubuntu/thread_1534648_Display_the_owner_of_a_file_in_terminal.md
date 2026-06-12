---
title: "Display the owner of a file in terminal??"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by victorhugo289 on 2010-07-19
Hi, I wanted to know how to display the owner of a file in terminal? Or if I get this right.. everything in my /home folder is mine and everything outside of it is supposed to be root??

---

### Post by munkyeetr on 2010-07-19
ls -la /path/to/file

you'll get something like this:
-rw-r--r--  1 jon  jon     300 Jul 18 12:11 .xinitrc

first jon is user
second jon is group

---

