---
title: "installing wvdial.deb for amd64"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by abirphs on 2010-06-28
I'm a beginner linux user. My processor is AMD 64x2 (4000+). I have installed 32 bit ubuntu 10.04 on it. now when i'm trying to install wvdial.deb amd64 version, it always says error: wrong architecture AMD64.

What should I do? should I install 64 bit ubuntu to overcome this problem?:confused:

---

### Post by Joe of loath on 2010-06-28
The architecture on a package refers to the OS that it should be installed on, not the processor. As you installed 32 bit Ubuntu, install the 32 bit package.

---

### Post by abirphs on 2010-06-28
thanks joe, but i also tried with ix86 version of wvdial, it didnt work. 
is there any other 32 bit version of wbdial?

---

### Post by Joe of loath on 2010-06-28
Have you tried installing from the repositories? ```
sudo apt-get install wvdial
``` should be all it needs.

---

### Post by abirphs on 2010-06-28
Dear Joe,

When I try to install, it gives this output

abir@Abir:~$ sudo apt-get install wvdial
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
abir@Abir:~$

---

### Post by Joe of loath on 2010-06-28
Firstly, try ```
sudo su
apt-get install wvdial
```

If that doesn't work,```
ps -ef | grep dpkg
``` and post the output.

---

