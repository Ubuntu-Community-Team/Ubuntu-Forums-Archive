---
title: "fail to install RAWTherapee"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by band1t on 2010-03-03
I have downloaded the Raw Therapee 3.0alpha1 and extracted it to home folder. I'm supposed to doubleclick the rt file but nothing happens?!](*,) 

I'm running 9.10 64-bit, fully updated.

---

### Post by band1t on 2010-03-04
Bump..

I have tried to enter terminal and run sudo apt-get update just before i doubleclick on the rt file but it wont start. I shouldn't have to log in as root to run rt files? I have checked properties that it is executable.

---

### Post by mikechant on 2010-03-04
What install steps (if any) did you follow before/after after extracting the files?
Can you list the file names in the extracted folder?

Can you try running the .rt file from the terminal? - this should give you some messages (just type ./rt to run it)

Also, this thread in the rawtherapee forums contains some possible help:
[http://www.rawtherapee.com/forum/viewtopic.php?t=1640](http://www.rawtherapee.com/forum/viewtopic.php?t=1640)
e.g have you tried running ./rtstart, do you need to run
sudo apt-get install libiptcdata
first, etc. etc.

---

### Post by moles on 2010-03-14
Try this ppa:
[https://launchpad.net/~rawtherapee/+archive/ppa](https://launchpad.net/~rawtherapee/+archive/ppa)

Installing Rawtherapee from there worked without problems for me.

---

