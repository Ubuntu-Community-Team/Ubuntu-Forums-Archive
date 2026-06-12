---
title: "Sleep Mode in Ubuntu 9.10"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by jhaveri.hiral on 2011-02-03
Hello All!

I am using Ubuntu 9.10 in my HP Pavilion Laptop.

When I SUSPEND the OS, close the flap of my laptop and then after few minutes re-open the flap, the OS does not start at all.

I only see the LEDs and nothing else on the screen. I waited for sometime, clicked some keys, clicked from trackpad, but nothing worked. 

Neither could I close my laptop directly from the power switch. I had to remove the battery to shut it down and start again..

So, I just want to know if there is any sort of SLEEP MODE available in Ubuntu 9.10 and if it is there then how can I use it???

Thank you in advance!!!

---

### Post by xoomer.ap on 2011-02-03
I never hibernate my computer since I became linux-user, therefore, maybe I'm wrong, but I know for hibernating (sleep mode) in Linux you should have your swap partition at least equivalent in Mb your RAM memory size.
2nd, I just typed: *apropos hibernate* in console:
```
pm-action (8)        - Suspend or Hibernate your computer
pm-hibernate (8)     - Suspend or Hibernate your computer
pm-is-supported (1)  - Test whether suspend or hibernate is supported.
pm-suspend (8)       - Suspend or Hibernate your computer
pm-suspend-hybrid (8) - Suspend or Hibernate your computer
```seems, command *pm-hibernate* - is that what you're looking for.

---

### Post by 3rdalbum on 2011-02-03
There are two sleep modes available: Suspend, and Hibernate.

Hibernate outputs the contents of RAM to the swap partition of the disk. It's very slow - it can be slower than a normal startup - and almost never works. Hibernating often causes the computer to crash, even when running Windows (so it's not just a Linux problem).

Suspend tends to work more often, on more types of computers. It does use a little power while suspended, and is much quicker than hibernation. However, it still doesn't always work; some computers might crash while suspending, or while resuming, or the hardware might be left in an inconsistent state so you need to remove the battery to reset things. It's very hardware dependent.

However, progress marches on. You're using Ubuntu 9.10, which is over a year old - ancient in Linux terms. Ubuntus 10.04 or 10.10 might have solved the problem for your particular computer. Try upgrading.

---

