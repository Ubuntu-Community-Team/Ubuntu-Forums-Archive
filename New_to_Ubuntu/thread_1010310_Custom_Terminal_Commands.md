---
title: "Custom Terminal Commands"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by KeilanS on 2008-12-13
Hey all,

I was wondering if there is a way to customize commands used in the terminal.

On the computers at my university (which run Fedora Linux), typing
```
e testing.txt
```
would open (or create) a file called testing.txt in emacs. So is there a way to change it so I can type e test.txt instead of emacs test.txt?

And I assume the answer will be similar, but I would also like to be able to type "ll" in place of "ls -l".

Thanks,
Keilan

---

### Post by taurus on 2008-12-13
You can edit ~/.bashrc

```
gedit ~/.bashrc
```
and add this line to the end of it.

```
alias e=emacs
```
Save it and then run 

```
source ~/.bashrc
e testing.txt
```
From now on, typing e from a terminal will bring up emacs, assuming that you have emacs installed.

---

### Post by jimmy the saint on 2008-12-13
[http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)

Check out the section on aliasing commands

---

### Post by KeilanS on 2008-12-13
Thank you both.

I will definitely read through the BASH tutorial. That should be most helpful.

---

### Post by cdtech on 2008-12-13
Heres a thread on "aliases" that might be helpful:
[http://ubuntuforums.org/showthread.php?t=679762](http://ubuntuforums.org/showthread.php?t=679762)

---

