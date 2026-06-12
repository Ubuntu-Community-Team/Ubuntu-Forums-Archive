---
title: "virtualbox conflict with KVM"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by medya on 2009-12-16
I installed one of those virtual machine applications for ubuuntu (qemu)

then my virtualbox stopped working , it said I have to recompile the header blah blah...

on the forums ppl told me to run this command and it works :
> sudo modprobe -r kvm-intel 

but the problem is each time I restart ubuntu I have to enter this command .

is there any way to remove kvm-intel permanently ?

---

### Post by cariboo on 2009-12-16
Open a terminal and type:

```
sudo apt-get purge kvm
```

That should get rid of it.

---

### Post by bodhi.zazen on 2009-12-16
> **cariboo907 said:**
> Open a terminal and type:

```
sudo apt-get purge [s]kvm[/s] virtualbox
```That should get rid of it.

Fixed that for you =)

@medya - yep, one or the other, not both.

---

### Post by medya on 2009-12-23
guys that doesnt work

---

### Post by bodhi.zazen on 2009-12-23
What problem are you having ?

---

### Post by johnjb on 2009-12-23
first you need bum so sudo apt-get install bum
then as root sudo su
then type bum
look for Full Visualization on i386 and amd 64 hardware and take the tick out of the box now enjoy

---

### Post by Paqman on 2009-12-23
> **medya said:**
> guys that doesnt work

Try:
```
sudo apt-get purge qemu-kvm
```

---

