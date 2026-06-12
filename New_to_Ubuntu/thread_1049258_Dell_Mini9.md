---
title: "Dell Mini9"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by stargazer926 on 2009-01-24
Hi, I am completely new to Ubuntu which came preinstalled on my Dell Mini9. I am stuck. I have been trying to figure out for hours how to update and install my software. Everytime I try I get the following error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.

Also, it seems that I can not locate my wireless network ANYWHERE on the system. 

Anyone have any ideas on how I can fix this? I don't mean to sound dumb, but a step by step fix is preferred since I know nothing about Ubuntu.

Thanks in advance for your help.

---

### Post by diablo75 on 2009-01-24
Click Applications>Accessories>Terminal.  Type in:

```
sudo dpkg --configure -a
```

That'll fix your package problem.

Your network manager icon (on the upper panel by the clock, looks like a couple of computers next to each other) should display nearby wireless networks by left-clicking on it.  If it doesn't, perhaps there's a button or switch on your laptop that has to be pushed to enable your wireless adapter before Ubuntu is allows to look for nearby networks to connect to.

---

### Post by llamabr on 2009-01-24
Hi.  I don't want to sound dumb, but did you open a terminal and type:

dpkg --configure -a

What are you doing to try to make your wireless work?  And what's it doing?

---

### Post by stargazer926 on 2009-01-24
Thanks!
I did'nt even know where to go to start typing in code. :redface: I think once I get the hang of this I will love Ubuntu. It sure sounds like eveyone out in these forums do! I have only used windows, so this is very different.

I think that may work. I will try when I get home (where my wireless network is)
Thanks again!

---

