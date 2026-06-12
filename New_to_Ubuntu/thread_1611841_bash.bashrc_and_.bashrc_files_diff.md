---
title: "bash.bashrc and .bashrc files diff"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by newport_j on 2010-11-02
What is the difference between the bash.bashrc and the .bashrc files?
 
Which one should I edit, when I want to change a path permanently for my perosnal use? 
 
Newport_j

---

### Post by DaithiF on 2010-11-02
bash.bashrc is global (for the entire system), .bashrc is per-user.

so change your .bashrc

---

### Post by newport_j on 2010-11-02
I only have bash.bashrc. So do I create a .bashrc from bash.bashrc? I can cp file bash.bashrc to bashrc and then edit. Will that do it? What else must I do to make it only my .bashrc file?
 
Newport_j

---

### Post by DaithiF on 2010-11-02
its 'your' .bashrc when its saved in /home/you/.bashrc
you don't copy it from anywhere, you just add whatever you want to a (blank) file.  you still inherit anything set in bash.bashrc

---

### Post by CharlesA on 2010-11-02
> **newport_j said:**
> I only have bash.bashrc. So do I create a .bashrc from bash.bashrc? I can cp file bash.bashrc to bashrc and then edit. Will that do it? What else must I do to make it only my .bashrc file?
 
Newport_j

Where are you finding thie bash.bashrc file?

The only one that should be in yer home directory is .bashrc.

---

