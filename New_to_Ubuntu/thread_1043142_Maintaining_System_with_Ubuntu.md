---
title: "Maintaining System with Ubuntu"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-18
Hi, i just installed ubuntu8.1 a few days ago.. i wanted to know how to maintain my system with ubuntu..we have disk defragment,disk check,removing duplicates and others in XP.. do we have any such tools here in ubuntu..thank you:)

---

### Post by jonabyte on 2009-01-18
No defag program needed, but updates are always good to run.

---

### Post by chethankrish on 2009-01-18
how can i increase my system performance.. do we have any tools to boost system performance..

---

### Post by Michael.Godawski on 2009-01-18
hi,

you do not need to run a disk defragmentation tool because of the specif partition format Ubuntu is using - ext3.


[LIST]
[*][http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)
[/LIST]
Actually you don't have to do anything like that. From time to time I run some basic terminal commands to remove not needed packages but that's it:

```
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by chethankrish on 2009-01-18
what does these commands do..
sudo apt-get clean
sudo apt-get autoremove

i'm sorry, am still a rookie..

---

### Post by binbash on 2009-01-18
> **chethankrish said:**
> what does these commands do..
sudo apt-get clean
sudo apt-get autoremove

i'm sorry, am still a rookie..

sudo apt-get autoremove , remove the packages which are not needed
sudo apt-get clean ,  clears out the local repository of retrieved package files

---

### Post by chethankrish on 2009-01-18
Thank YOU..BINbash

---

### Post by Shippou on 2009-01-18
You can see my post here:

[http://ubuntuforums.org/showthread.php?t=864729&highlight=howtos](http://ubuntuforums.org/showthread.php?t=864729&highlight=howtos)

Be warned though: you should know what you're doing. Although the guides are easy to follow, there is a high risk of losing data and breaking your system, as you are now meddling with the Linux equivalent of the registry (IMO). 

I guess you are a power user like me. You should try other distros geared for such users, maybe for example Wolvix (guys, don't flame me here; I am not an expert on distros, I am just recommending).

To all out there: please help this person.

---

