---
title: "remove xubuntu and xfce"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by psorincatalin on 2010-09-18
hey there forum

this is my 3rd post on this forum, i really enjoy linux in general and the *buntus in particular. anyway i'll jump right to the point

i have a really slow computer so i decided to try xfce with wubi (yes, still dual booting, but not for long), because if something goes wrong i can just uninstall xubuntu from windows. the thing is, i found that lxde desktop is lighter and i installed lxde - lubuntu on top of xfce - xubuntu and i want to keep only lubuntu.
 
1. how can i remove all of the xfce files, xubuntu desktop and everything that comes with xubuntu/xfce ?

2. every time i access synaptic, and my ntfs file systems, a notification pops up that's asking me for my password. is there any way i can remove that notification ?

i'm looking forward for your responses, thanks

---

### Post by wilee-nilee on 2010-09-18
> **psorincatalin said:**
> hey there forum

this is my 3rd post on this forum, i really enjoy linux in general and the *buntus in particular. anyway i'll jump right to the point

i have a really slow computer so i decided to try xfce with wubi (yes, still dual booting, but not for long), because if something goes wrong i can just uninstall xubuntu from windows. the thing is, i found that lxde desktop is lighter and i installed lxde - lubuntu on top of xfce - xubuntu and i want to keep only lubuntu.
 
1. how can i remove all of the xfce files, xubuntu desktop and everything that comes with xubuntu/xfce ?

2. every time i access synaptic, and my ntfs file systems, a notification pops up that's asking me for my password. is there any way i can remove that notification ?

**No passwords are for your protection you will have to get used to it.**

i'm looking forward for your responses, thanks

Okay here is a link to remove whole desktops make sure you choose the correct distro and desktop, and that you understand what your doing. feel free to ask questions.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

I forgot one thing here at the very end of the list there is this.
```
sudo apt-get install ubuntu-desktop
```
make sure you leave this out, and then run the lxde install again just to be sure nothing got removed that lxde uses.

---

### Post by psorincatalin on 2010-09-18
it worked!

thanks


what about the password thingie ?

---

### Post by wilee-nilee on 2010-09-18
> **psorincatalin said:**
> it worked!

thanks


what about the password thingie ?

So here is the downlow on the password. In Ubuntu your regular account is similar to a limited account in Windows. In Windows you can right click and run as a admin, with a password if you have one set. So to have admin right or root in Linux you have to use a password. It is just The way it is and I could be banned if I told you how to disable the password and run in root or have no password.

---

### Post by psorincatalin on 2010-09-18
okay thanks again for the help

---

