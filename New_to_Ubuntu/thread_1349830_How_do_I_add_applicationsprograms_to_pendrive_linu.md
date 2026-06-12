---
title: "How do I add applications/programs to pendrive linux?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by Scott_MacAdam on 2009-12-08
Hey everyone, 

I just got pendrive linux for a friend but he wants it so he can record music. I'm looking for a way to install Ardour on to my thumbdrive for him. I can't seem to find the synaptic package manager or add application tool. 

Thanks!

~Scott MacAdam

---

### Post by LowSky on 2009-12-08
If its a ubuntu or debian based distro then this should work

sudo apt-get install adour

otherwise what distro did you install?

---

### Post by Scott_MacAdam on 2009-12-08
I'm not even sure... I believe it is a minimalist remix of debain.

when using that code i get Bash: sudo command not found

---

### Post by LowSky on 2009-12-08
EDIT: Ok didn't realize but you spelled the application wrong when I searched for it
**Ardour **isn't in the debian repos, you will need to install it from the  website
 [http://ardour.org/download](http://ardour.org/download)

**FYI: Ubuntu Studio does have _Ardour _in its repos**

> **Scott_MacAdam said:**
> I'm not even sure... I believe it is a minimalist remix of debain.

when using that code i get Bash: sudo command not found


ok... that because Debian doesn't use Sudo by default, unless you configure it.

ok try this

open a terminal

type
```
 su
```
it will ask for root password, type it

then type
```
apt-get install *program*
```

*program *being whatever program you need. Hopefully it in Debian's repos

---

### Post by Scott_MacAdam on 2009-12-08
I could not get it using that code because it could not find it but I went on to the website and downloaded the Zip for the program and extracted it to my desktop. 

How do I go about running this?

Thanks for the help so far! You are a HUGE help to me.

---

