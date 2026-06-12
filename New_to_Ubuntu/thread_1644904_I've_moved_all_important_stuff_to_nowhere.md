---
title: "I've moved all important stuff to nowhere ? :/"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by lordmonkeyu on 2010-12-13
:cry:
I don't know how I did it but I manged to do something mega stupid namely 
```
monkey@patryk-ubuntu:/proc/1639/cwd$ sudo mv -t ./ /lib/firmware/
```and now nothing works (besides cd in terminal )
 I think if I restart my machine now it won't boot again....

Is it possible to recover my mistake ?
and I don't know why but i can do this recursive cd
```
monkey@patryk-ubuntu:/proc/1639/cwd/proc/1639/cwd$ cd proc/1639/cwd/ proc/
monkey@patryk-ubuntu:/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd$ cd proc/1639/cwd/ proc/
monkey@patryk-ubuntu:/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd$ cd proc/1639/cwd/ proc/
monkey@patryk-ubuntu:/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd$ cd proc/1639/cwd/ proc/
monkey@patryk-ubuntu:/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd/proc/1639/cwd$ cd proc/1639/cwd/ proc/

```

---

### Post by mr clark25 on 2010-12-13
it looks like you moved the entire contents of your home directory to /lib/firmware/   .

I'm not sure how someone would fix this, but i would try this:
```
cp /lib/firmware ~/
```


do you have any valuable data on this install of ubuntu?

---

### Post by lordmonkeyu on 2010-12-13
Fortunately no ;) I have just installed it 4 hours ago ( because I was getting pissed off when a lot of things wouldn't work on virtualbox - win 7 as host)
but now I cannot even boot it :/ (I have restarted to win7 ) but I will reinstall it tomorrow.

---

### Post by low_rider on 2010-12-14
First off, a little correction:
mv -t ./ /lib/firmware/ took all the files from /lib/firmware and moved them to /proc/1639/cwd.

As for the recursive cd, cwd is usually a sym-link so you are probably just going back to the same place over and over.

For a fix:
If you want to just reinstall, that will most likely solve your problem with minimal hassle.
If you're like me and refuse to be defeated, try booting from a live CD and mount your hard drive that way.  You should have all the bash commands and may be able to reverse your mv command.

---

