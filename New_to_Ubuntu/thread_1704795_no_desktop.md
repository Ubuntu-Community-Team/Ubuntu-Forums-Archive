---
title: "no desktop"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by amalnath on 2011-03-11
hi,
 i have installed maverick onto a lenovo b460 laptop using wubi.
 But when i boot into maverick, there is no desktop, only the CLI (which asks for username&password).
I tried '*sudo apt-get install ubuntu-desktop*', but it says ubuntu desktop is already installed.
But everything works fine in live session(no display problem).What to do??:-k
 any help is appreciated..........

---

### Post by el_koraco on 2011-03-11
try typing startx in the cli

---

### Post by Hippytaff on 2011-03-11
What graphics card do you have?
 
try ```
sudo service gdm start
```
 
[This might be worth a read]("http://ubuntuforums.org/showthread.php?t=1639198")

---

