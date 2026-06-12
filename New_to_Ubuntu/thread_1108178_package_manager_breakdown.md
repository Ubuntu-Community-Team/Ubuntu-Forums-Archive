---
title: "package manager breakdown"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by mroels on 2009-03-27
Hello,

Few days ago I installed Amarok and noticed I missed a few codecs to make the software run. I looked for the right code and entered it in the terminal, but now my package manager reports:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I can no longer install updates, nor open the package manager and Amarok doesn't function anymore either. I suppose I should have been more careful and not just copy the sudo's I found on the web for the Amarok codecs. Could anybody help me out? I have no clue what to do. 

Many thanks in advance! 

Maarten

---

### Post by Nero147 on 2009-03-27
one quick and easy fix that might work is type into a terminal
sudo apt-get install -f
This will try to fix your package list. It usually works for me.

---

### Post by maddog39 on 2009-03-27
Well you have to do what the error tells you to do. Open a terminal and run the command:
```

sudo dpkg --configure -a

```
Then everything should be back to normal.

---

### Post by SunnyRabbiera on 2009-03-27
a very common issue, but very easy to fix.
Open a terminal and copy and paste this command:
sudo dpkg --configure -a

but please make sure you dont have a package manager open :D

---

### Post by mroels on 2009-03-27
> **SunnyRabbiera said:**
> a very common issue, but very easy to fix.
Open a terminal and copy and paste this command:
sudo dpkg --configure -a

but please make sure you dont have a package manager open :D

Thanks folks! I used this sudo before, but i must have typed it wrongly as it works fine now.

M.

---

