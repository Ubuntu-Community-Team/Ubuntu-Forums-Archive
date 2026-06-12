---
title: "bitchX"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by thinkLinuX on 2010-10-30
Hi i need help installing the bitchx in ubuntu. i download it from bitchx.org and compile it. But it can compile cause it has error. I try the sudo apt something, it also didnt work. any advise?

---

### Post by Rubi1200 on 2010-10-30
Did you install it using these instructions?:
> _How to install BitchX?_

$ wget [www.bitchx.com/download/ircii-pana-1.1-final.tar.gz]("http://www.bitchx.com/download/ircii-pana-1.1-final.tar.gz")
$ tar xvfz ircii-pana-1.1-final.tar.gz
$ cd BitchX
$ ./configure
$ gmake
$ gmake install_local[http://www.bitchx.com/faq.php](http://www.bitchx.com/faq.php)

Also, make sure you put it in a directory that is convenient for you. By default, downloads will probably be in the Downloads folder.

 > But it can compile cause it has errorPost the error message please.

---

### Post by CharlesA on 2010-10-30
There is also a cli IRC client called pork in the repos.

---

### Post by thinkLinuX on 2010-10-30
onfigure: WARNING: cannot find setupterm - trying tgetent
checking for tgetent in -ltermlib... no
checking for tgetent in -ltermcap... no
checking for tgetent in -lcurses... no
configure: error: cannot find setupterm or tgetent

---

### Post by Rubi1200 on 2010-10-30
Do you have the **build-essential **package installed?

Check that first and then try again.

---

### Post by thinkLinuX on 2010-10-30
yup i did that already, thats the outcome

---

### Post by Rubi1200 on 2010-10-30
Okay, next:
install the following package:
ncurses-term

You might also want to check if you have **libterm-query-perl** and **libncurses5-dev **installed too.

By they way, this seems like an awful lot of work when you could just install Pork, as suggested above by CharlesA.

---

