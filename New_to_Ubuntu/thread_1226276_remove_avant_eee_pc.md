---
title: "remove avant eee pc"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by llamabr on 2009-07-29
Hello.  I'm trying to uninstall the very annoying avant dock on my fresh install of ubuntu on my asus eee pc.  can anyone explain the following behavior?  Thanks

```
anlys@mini:~$ ps aux | grep avant
anlys     5417  0.1  2.7  27308 14148 ?        S    12:21   0:01 /usr/bin/avant-window-navigator
anlys     5651  0.0  0.1   3236   792 pts/0    S+   12:30   0:00 grep avant
anlys@mini:~$ sudo apt-get remove avant-window-navigator 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package avant-window-navigator is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anlys@mini:~$ 
```

---

### Post by llamabr on 2009-07-29
Hmm.  I seem to have stumped you all.

Putting the question a different way, how can I remove this from my desktop.  I've tried add/remove, and it told me there's a conflict, and I should use synaptic.  When I tried to apt-get install it, so that i could then apt-get remove it, it says there are unmet dependencies, and it would not install.

I've also unclicked the little box that says 'automatically start awn on login', but it still starts, strangely.

As it is, I just have to right click and close it every time I log in.  How annoying.

---

### Post by llamabr on 2009-07-31
Still stumped, eh?

As a workaround, I've added a 
```
killall avant-window-navigator 
```
to my .bashrc

sloppy, but it kills it until I can remove it.

---

### Post by llamabr on 2009-08-01
Maybe I can take a razor blade to the part of the disk where the program exists?

---

### Post by YesSir on 2009-08-01
You should be able to remove it by uninstalling in the add / remove software in the applications menu..

---

### Post by llamabr on 2009-08-02
> **YesSir said:**
> You should be able to remove it by uninstalling in the add / remove software in the applications menu..

Certainly should, and yet, it's not there.

Anyway to explain the behavior one sees in the first panel (above)?

---

### Post by mikechant on 2009-08-02
What does synaptic show if you use the search function (not the quick search) to look for anything with 'avant' in it? Does it show the package as installed or not show it at all?

---

### Post by llamabr on 2009-08-02
Hi.  Thank you, I believe that did it.  I found something called:

```
avant-window-navigator-bzr
```

and removed it (completely).

I've been at this for many years, and I've never used synaptic before, always opting for the cli to install/remove.  I'm sure that I could have searched for this with apt-get, but I don't know how.

Well done, and thanks for the assistance.

---

### Post by LewRockwell on 2009-08-02
it can be frustrating indeed

.

---

