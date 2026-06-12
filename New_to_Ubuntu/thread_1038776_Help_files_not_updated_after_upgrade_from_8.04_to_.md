---
title: "Help files not updated after upgrade from 8.04 to 8.10"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-01-13
Hi!  After three months of using 8.10, I am just now noticing that anywhere in the help files where 8.10 or Intrepid should be are just blank.  There are also some outdated instructions for packages that are no longer supported.  It is almost like my documentation is stuck somewhere between 8.04 and 8.10, like some weird Heron-Ibex hybrid!

Anything I can do to correct this?  I have all updates installed.

Thanks in advance!

---

### Post by gettinoriginal on 2009-01-15
First, your software sources should look like the attached screenshot. :P
[ATTACH]99912[/ATTACH]
Then in terminal do:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by pi.boy.travis on 2009-01-15
> **gettinoriginal said:**
> First, your software sources should look like the attached screenshot. :P
[ATTACH]99912[/ATTACH]
Then in terminal do:
```
sudo apt-get update && sudo apt-get dist-upgrade
```


Thanks for the reply!

I don't usually install any backports, as they are unsupported.  Should I anyway?

As it is, the backports didn't contain any upgrades pertaining to Yelp or any help files, and redoing dist-upgrade didn't do it either.  Anything else I can do?

---

### Post by gettinoriginal on 2009-01-16
When you click a help button, does it open a blank window, or does it say "not installed"

---

### Post by pi.boy.travis on 2009-01-16
> **gettinoriginal said:**
> When you click a help button, does it open a blank window, or does it say "not installed"

Neither, but it usually displays outdated information.  There are even some pages for packages that are no longer maintained.

---

### Post by gettinoriginal on 2009-01-16
I do apologize, but I am at a loss.  If I were you, I would simply go into synaptic and type "help" into the search, and check to see which help files are installed.  :confused:

---

### Post by pi.boy.travis on 2009-01-17
> **gettinoriginal said:**
> I do apologize, but I am at a loss.  If I were you, I would simply go into synaptic and type "help" into the search, and check to see which help files are installed.  :confused:


Thanks!  Reinstalling ubuntu-docs did the trick!

---

