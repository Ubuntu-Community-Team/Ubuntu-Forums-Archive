---
title: "my ubuntu seems to have display problems."
date: 2009-05-02
forum: New to Ubuntu
---

### Post by jwee5467 on 2009-05-02
Hi there.

Well as it seems, i have just installed ubuntu after months of speculation on whether i change to ubuntu after someone previously installed xubuntu on the same machine.

It have an old ibm thinkpad x30 with 1 gb ram and 1.2 ghz.

Anyway, what happens is after i boot up it seems fine. However, after a short period of time, random letters like 'b' have a grey/black rectangle that surrounds them and it makes it impossible to read anything or do any work!!!

I have a screenshot here. 

[IMG]http://ubuntuforums.org/home/john/Desktop/Screenshot.png[/IMG]

---

### Post by Sealbhach on 2009-05-02
Does it happen just in your browser? Or in other applications as well?


.

---

### Post by jwee5467 on 2009-05-03
eventually happens in all apps. was thinking that maybe to do with fonts atm. also tried getting a similar old thinkpad that i have and boot xubuntu via wubi on it. same problems.

---

### Post by Sealbhach on 2009-05-03
Have you installed the Microsoft fonts package?

You can find it in Synaptic or install from the terminal:

```
sudo apt-get install msttcorefonts
```

It might fix it.


.

---

### Post by jwee5467 on 2009-05-06
but the display is more on the fonts alreadly installed? im struggling to understand how it would help... i guess would it work if i changed my display fonts to one of the ones installed?

---

