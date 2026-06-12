---
title: "Spread Toolkit"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by nauman.mustafa on 2011-02-08
Dear All,

I am quite new to Ubuntu. I need your help about Spread tool kit. I have downloaded user.c program from internet (Spread's site) I dont know how to run that files with extension ".c " Any body please help me.

---

### Post by sandyd on 2011-02-08
> **nauman.mustafa said:**
> Dear All,

I am quite new to Ubuntu. I need your help about Spread tool kit. I have downloaded user.c program from internet (Spread's site) I dont know how to run that files with extension ".c " Any body please help me.
a) don't download apps from the internet if their already in the repos, apps from the internet conflict with apps from the repos occasionally, and it just causes a big huge mess.

b) spread is already in the repos, however, the system sources is hidden. Open Synaptic, and click on "Software Sources".

Make sure all the checkboxes in the first tab are checked (i.e. universe, multiverse, main ubuntu repos)

After clicking "ok", press the "reload" button on synaptic.
then install the spread package.

Which reminds me, I have to add this to brainstorm.

---

### Post by nauman.mustafa on 2011-02-09
Yes They are all clicked and working. I installed spread through the following command on terminal:

sudo apt-get install spread.


I just to know one thing: When there is a file of getedit with extension ".c" How to use it. It has a program written in language C.

---

### Post by sandyd on 2011-02-09
> **nauman.mustafa said:**
> Yes They are all clicked and working. I installed spread through the following command on terminal:

sudo apt-get install spread.


I just to know one thing: When there is a file of getedit with extension ".c" How to use it. It has a program written in language C.
compile it with gcc/g++

---

