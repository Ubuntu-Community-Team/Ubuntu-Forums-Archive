---
title: "Installation Problem"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-04-05
When ever I try to install application through terminal i get this error message!! pls help me out

[B]kevin@sreenivassudarshan-desktop:~$ sudo apt-get install clamav
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
kevin@sreenivassudarshan-desktop:~$ sudo apt-get install koffice
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
kevin@sreenivassudarshan-desktop:~$ [/B]



thanq you

---

### Post by zeroseven0183 on 2010-04-05
Hi! There seems to be an error installing an application. Please run
```
sudo dpkg --configure -a
``` in the Terminal to correct this.

Try also ```
sudo apt-get install -f
```.

---

### Post by 1991sudarshan on 2010-04-05
thanq you problem solved

---

### Post by zeroseven0183 on 2010-04-05
Sure. My pleasure helping you. :-)

*Could you please mark this thread as SOLVED. Thanks*

---

### Post by 1991sudarshan on 2010-04-05
sorry i marked it now!!!!!!!!!!

---

