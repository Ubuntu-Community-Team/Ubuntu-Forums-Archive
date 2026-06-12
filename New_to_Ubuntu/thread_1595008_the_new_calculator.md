---
title: "the new calculator"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by rosswmcgee on 2010-10-12
The old calculator I could put the icon on my taskbar and when opened it 

would appear on the desktop where I wanted it to, which is the lower right 

hand corner. The new calc cannot be resized and will always open up in the upper left and I have to

then move it to the lower right. After I close it and re-open it then 

appears again in the upper left again. Any ideas on how to make it open

where I want it to and to resize it??

If you install Galculator at least it is adjustable, but it has a bug the divisor won't work.

I do think there is a time for the Ubuntu gods to leave well enough alone.

---

### Post by rburkartjo on 2010-10-13
ross i dont think there is a way i also tried the default calculator and it opens on the upper left as does the one i use
Qalculate

---

### Post by rosswmcgee on 2010-10-13
Interesting that may be the case, so what did they not do in 10.10 that they did in 10.04??

---

### Post by rburkartjo on 2010-10-14
only the programing gods know the answer to that question

---

### Post by rosswmcgee on 2010-10-14
That is what happened in Fedora as well. Mint still works the way I want. However if any one figures out a fix please post it. If you install Galculator at least it is adjustable. However the divsor does not work.

---

### Post by rosswmcgee on 2010-10-23
> **rburkartjo said:**
> only the programing gods know the answer to that question
The God's Reply

"Bug 659624" <659624@bugs.launchpad.net>


I'm marking this bug as a regression, the gcalctool in Ubuntu 10.04 did
remember its position.
 
** Changed in: gcalctool (Ubuntu)
       Status: New => Confirmed

---

### Post by HermanAB on 2010-10-23
Howdy,

Check whether the calculator has a -geometry argument and if so, add it to the launch string.

---

### Post by rosswmcgee on 2010-10-23
Thanks for the idea but I have no knowledge of how to do what your recommend, and why would that allow the calc to stay put?

---

