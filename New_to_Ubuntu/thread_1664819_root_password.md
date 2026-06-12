---
title: "root password"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by robotz421 on 2011-01-11
Hi.    I have just installed Ubuntu on a new machine.  I can log in fine using my user account but I need root priviledges to do some administration.  Ubuntu does not accept the password I used for installation.  Is there a default root password for new installations or is there some way I can find or reset the root password?

---

### Post by bou3lam on 2011-01-11
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by blind2314 on 2011-01-11
Appending sudo to your commands and then using the password setup for your personal user account should accomplish what you want. For example,
 
```
sudo chmod 775 /dir
```

---

### Post by Rubi1200 on 2011-01-11
Hi and welcome to the forums :)

When you say it does not accept your password, what exactly do you mean?

if you are typing it in the terminal you will not see anything (what you type is not echoed).
Just type the password and hit Enter.

If you mean the password is not accepted at all, that is another matter.

---

### Post by Rusty au Lait on 2011-01-11
No, no, no. Do not change your root password.
If you need to stay root for chores do this:
sudo su
<your password here>
this makes you root. Use "exit" to return to yourself.
If you are in a GUI get the package that performs root functions. I have forgotten the package name. You should be able to find it at help.ubuntu.com

---

### Post by bodhi.zazen on 2011-01-11
> **Rusty au Lait said:**
> No, no, no. Do not change your root password.
If you need to stay root for chores do this:
sudo su
<your password here>
this makes you root. Use "exit" to return to yourself.
If you are in a GUI get the package that performs root functions. I have forgotten the package name. You should be able to find it at help.ubuntu.com

Ubuntu uses sudo and 

```
sudo -i
``` is preferred over other methods (sudo su, sudo -s, etc).

For graphical applications use gksu

When you enter your password, nothing appears in the terminal as you type, just type your pw and hit enter.

---

### Post by robotz421 on 2011-01-11
Thanks for the welcome Rubi1200.  bou3lam that link explained what was going on and helped untangle my confusion.  I was using just su and Ubuntu asked for the root password which of course didn't work.  Sudo -i seems to work fine.  What do I do if I want to drag and drop some files from one window to another?  I want to use a GUI but I don't necessarily know the names of all the apps I want to use to invoke them from the command line.

---

### Post by bodhi.zazen on 2011-01-11
> **robotz421 said:**
> Thanks for the welcome Rubi1200.  bou3lam that link explained what was going on and helped untangle my confusion.  I was using just su and Ubuntu asked for the root password which of course didn't work.  Sudo -i seems to work fine.  What do I do if I want to drag and drop some files from one window to another?  I want to use a GUI but I don't necessarily know the names of all the apps I want to use to invoke them from the command line.

gksu nautilus

---

### Post by robotz421 on 2011-01-11
:popcorn:Wonderful!  You guys are great.  That solves all my problems.

---

