---
title: "ubuntu wont load gui after login"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Velenjak on 2011-02-24
problem solved - thanks for help!!!
 
 
 
 
 
 
 
so im using an old dell dimension 8400...
 
ubuntu 9.10
 
 
i was backing up my files earlier today when my computer crashed (too much use - whenever i give it too much stress it just crashes)
 
it kept saying that it couldnt mount the drive. after much fighting i ran fsck (or something like that) and it fixed the problem.
 
so i logged back in, and tried to backup files again.... bad mistake. it crashed - i cant transfer too many files at once i guess .... (it was only a couple GBs - is this an indication that some of my hardware is starting to die?)
 
now it boots fine, but when i login it sits on the default screen. my desktop does not load 
 
i ran thru the command prompt and updated all files - i also ran the command to check for new graphics drivers. still doesnt work.
 
any ideas? i really need help... i have to email my professor with an assignment before i go to sleep... id love to be able to login and send it 
 
thanks in advance.

---

### Post by darknomel on 2011-02-24
Can you get to the text login? Then you should be able to log in and copy the files to a USB stick and email it from a working PC?

---

### Post by zenwalker on 2011-02-24
Did you try re-installing your desktop environemnt packages if in case if its corrupted. But i guess some thing else is problem, may be as you said ur home dir is corrupted.

---

### Post by ankit singh on 2011-02-24
Try resetting your gnome settings
Hit ctrl+alt+f1 and login or alt+f2

and type this

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

after that logout or reboot

---

### Post by Velenjak on 2011-02-24
> **darknomel said:**
> Can you get to the text login? Then you should be able to log in and copy the files to a USB stick and email it from a working PC?
 
 
i have very little experience with the command line - i wouldn't even know where to begin....

---

### Post by zenwalker on 2011-02-24
When you get your login screen, just press Ctrl + Alt + F<1-7> keys to get ttys also called terminals. There you can login and get the files off to your USB

---

### Post by darknomel on 2011-02-24
> **ankit singh said:**
> Try resetting your gnome settings
Hit ctrl+alt+f1 and login or alt+f2

and type this

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```after that logout or reboot

Try this first, if that doesn't work, we can help you to copy the files using the command line :)

---

### Post by Velenjak on 2011-02-24
> **zenwalker said:**
> When you get your login screen, just press Ctrl + Alt + F<1-7> keys to get ttys also called terminals. There you can login and get the files off to your USB
 
i was able to login, but im at a dead end here... i remember where the file is location - but i cant get past the home/[myusername]/ 
 
i tried home/[username]/documents etc. etc. but i cant get past this initial tier... what else am i missing?

---

### Post by Velenjak on 2011-02-24
> **ankit singh said:**
> Try resetting your gnome settings
Hit ctrl+alt+f1 and login or alt+f2
 
and type this
 
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
 
after that logout or reboot
 
 
nevermind previous post
 
 
this worked!!!!!!!! thank you very much

---

