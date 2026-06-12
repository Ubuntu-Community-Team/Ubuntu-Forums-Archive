---
title: "update fail what to do now"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by larruss on 2009-01-19
Just installed and was loading updates and locked up. Tried to run again and got this message.





E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Now what to do? firefox won't open either now.

Thx

---

### Post by taurus on 2009-01-19
Close down the update window manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Titan8990 on 2009-01-19
I am going to teach you something very important about Linux. Unlike Windows where error messages are a bunch of useless crap that leads you in a wild goose chase, Linux error messages are almost always useful and should be examined closely.

So lets examine your error message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```


This error message tells us to manually run 'dpkg --configure -a' and that is exactly what we are going to do. 

Go to Application -> Accessories -> Terminal

Type the follow and hit enter:

sudo dpkg --configure -a


Edit: 2nd time today taurus....

---

### Post by taurus on 2009-01-19
> **Titan8990 said:**
> I am going to teach you something very important about Linux. Unlike Windows where error messages are a bunch of useless crap that leads you in a wild goose chase, Linux error messages are almost always useful and should be examined closely.

So lets examine your error message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```


This error message tells us to manually run 'dpkg --configure -a' and that is exactly what we are going to do. 

Go to Application -> Accessories -> Terminal

Type the follow and hit enter:

sudo dpkg --configure -a


Edit: 2nd time today taurus....

Did you have this message save up somewhere because this is at least the second time today that you've replied with the exact same thing, word per word (except the last line)?  ;)

---

### Post by pdtpatrick on 2009-01-19
Well i'll understand why he would save it before there has been more of these posts lately or since ive been on this forum. I guess i cant say more since i have nothing to compare it against :)

---

### Post by Titan8990 on 2009-01-19
Actually, no, these come often enough that it is easy to find my last thread that I replied to the topic in :). I used to use tomboy notes in Linux and (before my time with Linux) keynotes in Windows. I would put common responses to errors such as this one in different notes.


Going by the fact that this is word for word what you posted last time:

> Close down the update window manager. Then, open a terminal and run

Applications -> Accessories -> Terminal
Code:

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```


That you do something similar :).

---

### Post by taurus on 2009-01-19
> **Titan8990 said:**
> 
Going by the fact that this is word for word what you posted last time:

That you do something similar :).

Yip.  Typed the whole thing myself each and every time.  ;)

---

