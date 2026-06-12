---
title: "Can't add a new user (9.04)"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by zcacogp on 2009-05-08
Chaps, 

I'm probably going to make an idiot of myself for asking this, but how do you add a new user to Ubuntu? 

I'm running 9.04 (JJ), and if I go to "System > Admin > Users and Groups", I see the list of users (just me), but the "Add new user" button is greyed-out. 

When I try putting ```
sudo users-admin
```into the terminal (as has been suggested on another thread), the same window pops up and the terminal tells me ```
CRITICAL **: Unable to lookup session information for process '12597'
```(which sounds like bad news to me!) 

What am I doing wrong? 


Oli.

---

### Post by Kareeser on 2009-05-08
You first need to unlock the users-admin session from the dialogue itself. See the button labelled "Unlock"? :)

Don't run the program under root.

---

### Post by zcacogp on 2009-05-09
Kareeser, 

See! See! I *told* you I was going to make an idiot of myself asking that question! 
[SIZE="1"]
(Thanks. That solved the problem very nicely. I really am an idiot, aren't I?) 
[/SIZE]

Oli.

---

### Post by Exarch on 2009-05-14
Did this solve your problem?

I have the exact same issue and cannot get the users-admin to unlock. Whether I start it as a limited user or as a root, I get a window with everything grayed out (including the Unlock button) and when I mouseover the Unlock button I get a popup "This action is not allowed" (very helpful :D )

The Help button is accessible but only leads to a relatively useless 3 page documentation with no information about how to unlock the window.

---

### Post by Carl Hamlin on 2009-05-14
Easier still - crack open a terminal.

```

you@yourcomputer:~$ sudo adduser username

```

---

### Post by bacardiandwatermelon on 2009-05-14
Did they add the unlock button in hardy? It kept me guessing for a few minutes the first time I came across it. :-P

---

### Post by Bobrm2 on 2009-09-13
> **Carl Hamlin said:**
> Easier still - crack open a terminal.

```

you@yourcomputer:~$ sudo adduser username

```
User-admin's unlock is grayed out? adding a new user and root is grayed out(?). I believe this is the problem with inaccessable programs in Main Menu or Alacarte. You help appreciated. TIA

---

### Post by Sb1 on 2009-11-12
Thanks this helped me out too (9.10)

I'm dual booting with an old laptop and this is my 1st REAL time using it.  Being playing around for 20-90 min. every 6 months or so.  But keep forgetting since don't stick with it.

This time planning on keeping it with WinXP SP3.

---

