---
title: "download gift folder"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by ragia on 2009-06-21
hi all
I am new to ubuntu
i need to undersgtand the follwoing line and how to execute it from ubuntu 

cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/sources/gift co gift
thanks in advance

Ragia

---

### Post by ad_267 on 2009-06-21
CVS is a version control system. It is designed for maintaining the source code of an application. You can open a terminal from Applications - Accessories - Terminal. Then install cvs by running:
```
sudo apt-get install cvs
```
You will have to enter your password (note nothing will appear when you type though).
Then you can enter that command.

What that command does is checks out (co) the /sources/gift directory from the cvs.savannah.gnu.org server into the "gift" directory. I'm not sure what the -z3 option does as I haven't used CVS myself, but you can run "man cvs" to find out.

---

