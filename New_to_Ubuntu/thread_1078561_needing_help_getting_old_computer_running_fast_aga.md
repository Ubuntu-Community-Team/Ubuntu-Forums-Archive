---
title: "needing help getting old computer running fast again"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by ChrisinCa on 2009-02-23
I am not sure what section to ask this question but I am an absolute beginner so maybe this is the best place.

I have an older computer with a Pentium 3 processor that I am forced to use as my home computer but that is okay because ubuntu runs has run very well on it, until now. I have added software packages (I am a musician > ubuntu studio, & games), I have changed appearance settings (window colors mainly), and have added half a dozen firefox extensions to my browser. Now the computer is running as slow as it did when it had windows 2000 installed, both offline and online.

My question is what can I keep and what should I lose? I will probably just re-install ubuntu but before I do I want get some idea of what programs I must avoid on a slow computer.

Thanks in advance, Chris

---

### Post by echo314 on 2009-02-23
Certain programs will be requirement intensive, and there is no easy way around that. If you post what specific programs, we might be able to suggest alternatives that are lighter on recourses. They might not be exactly the same, but if performance is important to you than I'm sure you will learn.

You could also try using a lighter version of Ubuntu from the get go. Xubuntu uses a display manager that requires less resources then Gnome or KDE, so you might want to try that. All packages that you are using now will work in Xubuntu as well.

---

### Post by roccivic on 2009-02-23
Try some other Linux distribution.
E.g.: Puppy linux, Damn Small Linux or similar

---

### Post by matteojg on 2009-02-23
(Assuming you have GNOME)

With no programs running go to System>Admin>System Monitor

Under Resources:
How much RAM do you have available?
How much RAM is being used?
CPU?
What is the size of your SWAP and how much is in use?

Under File Systems:

What is the size of your HD and how much is used?

Under Processes:

Check under status...is anything listed as "zombie"?
Does anything look like its using more RAM than it should (sign of a possible memory leak)
Are any processes running that you don't need, e.g. something for managing blue tooth connections when you have no blue tooth devices?

Some additional things to check:

System>Preferences>Appearance>Visual Effects

And how many applets do you have running in your task bars?

---

