---
title: "hurt grub"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by nnjond on 2009-03-01
Hi, can any one help me ?

I've added openSuse to my pc. all seemed to go well while installing:

sda1 ubuntu,sda3 opensuse, sda5 a shared swap.

openSuse has become the default at boot. When i arrow down and hit ubuntu,  i get 
Error 15.

-before the familar grub scrn appears.

Should there only be one answer to this command?

find /boot/grub/stage1 

(hd0'0)
(hd0,2)

---

### Post by abhiroopb on 2009-03-01
I have no idea what the problem is...but typing "error 15 grub" into google presents a pretty good answer :)

[http://www.linuxquestions.org/questions/fedora-35/grub-error-15-431469/](http://www.linuxquestions.org/questions/fedora-35/grub-error-15-431469/)

---

### Post by nnjond on 2009-03-01
Thanks for your interest; I'm sorry that page didn't help me at all.

---

### Post by JoshuaRL on 2009-03-01
> **nnjond said:**
> Thanks for your interest; I'm sorry that page didn't help me at all.

It should.  Did you try those steps laid out there?  If so and it didn't work, where did it fail?  What were the errors output?

---

### Post by louieb on 2009-03-01
> **nnjond said:**
> Should there only be one answer to this command?

```
find /boot/grub/stage1 

(hd0,0)
(hd0,2)
```
  
Twice would be right. One for the Ubuntu install, one for Suse. stage1 is a copy of the code grub puts in the MBR

Try this entry in your OpenSuses'  Grub configuration file. 

```
title Load the Ubuntu menu.lst
configfile (hd0,0)/boot/grub/menu.lst 
```More here [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")  ( do a searh on this page for **configfile**)

---

### Post by nnjond on 2009-03-01
Your  solution seems to be the simplest. Please tell me how do i get to Grub configuration file. from the cl?

---

### Post by louieb on 2009-03-02
Just a guess - haven't used OpenSuse.  1st: su to root, 2nd: edit with nano   
```
su
nano /boot/grub/menu.lst
```If you were using Ubuntu
```
sudo nano /boot/grub/menu.lst
```

---

### Post by sahabcse on 2009-03-02
Hi

For fixing the grub follow below ur

==============================
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
=============================

Sahab

---

