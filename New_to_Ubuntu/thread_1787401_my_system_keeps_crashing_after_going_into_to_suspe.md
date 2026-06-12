---
title: "my system keeps crashing after going into to suspend mode"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by werty2010 on 2011-06-21
when i reopen the lid after i leave my laptop in suspend mode for some hours,i think it crashes...
i can see some leds continuing to be turned on,indicating that it responds to the opening of the lid but after that no matter what i press all i can see is a black screen...
some help?

---

### Post by jtarin on 2011-06-21
First turn off your screen saver.....then report back if it still happens.

---

### Post by werty2010 on 2011-06-21
> **jtarin said:**
> First turn off your screen saver.....then report back if it still happens.

it doens't happen all the time. usually when it is suspended for more than 5-6 hours.
i'll be happy to try it and report back...

---

### Post by Spae on 2011-06-21
Mine does it to. And i don't have a screen saver.

My solution: don't use the suspend function.

---

### Post by werty2010 on 2011-06-21
> **Spae said:**
> Mine does it to. And i don't have a screen saver.

My solution: don't use the suspend function.

this is just avoiding the problem, not a solution

---

### Post by wildmanne39 on 2011-06-21
> **werty2010 said:**
> this is just avoiding the problem, not a solution
Hi, you can have a look at this link on freezing.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by misterbiskits on 2011-06-21
> **spae said:**
> mine does it to. And i don't have a screen saver.

My solution: Don't use the suspend function.

+1.

---

### Post by werty2010 on 2011-09-03
i did a reinstall the last week and the problem is still there..
i noticed that it usually appears when the laptop is suspended for long periods of time.

i use the suspend function quite often so if someone has a solution i would appreciate it

---

### Post by 2F4U on 2011-09-03
I had a similar problem with suspend/hibernate on an old laptop with ATI graphics card. Due to the age I had to use the open source driver. After some tinkering I found that the solution for me was to add nomodeset to the grub kernel line. This parameter disables kernel mode setting (KMS) so the boot screen doesn't look as nice as it could, but it fixed my problems with suspend/hibernate on that machine.

---

### Post by Sotanaht on 2011-09-03
There's a package that fixes the suspend/hibernate functions on many laptops.  I'll have to look it up later unless somebody else posts it.  No time right now

---

### Post by Sotanaht on 2011-09-04
the package is called uswsusp, and you can install it by opening a terminal (ctrl-alt-t) and entering
```
sudo apt-get install uswsusp
```
after rebooting, I believe it should stop having the issue, but if it doesn't, try running *sudo s2ram* in a terminal.  If that does work, read this thread
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)
If it doesn't, then I'm out of ideas.  Read the thread anyway, maybe it has another solution further into the thread than I've read.

---

