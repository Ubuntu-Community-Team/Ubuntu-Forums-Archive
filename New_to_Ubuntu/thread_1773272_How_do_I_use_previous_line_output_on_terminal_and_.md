---
title: "How do I use previous line output on terminal and feed it back as input?"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by gotomstergo on 2011-06-01
For example, if I type,

$ *program*
The program '*program*' is currently not installed.  You can install it by typing:
sudo apt-get install *program*

but instead of retyping or copying the last line (sudo apt-get...), is there a lazy way to feeding that line as input?

---

### Post by SoFl W on 2011-06-01
Use your mouse and highlight the text you want copied, and then right click to copy, right click to paste.

---

### Post by drs305 on 2011-06-01
Or even highlight, middle click to paste (if you have one).

---

### Post by lombardoja on 2011-06-02
I may be reading the question incorrectly but can't you just hit the up arrow?

---

### Post by alphacrucis2 on 2011-06-02
> **lombardoja said:**
> I may be reading the question incorrectly but can't you just hit the up arrow?

Up arrow recalls previous input but not output.

---

### Post by DaithiF on 2011-06-02
```
sudo apt-get install !$
```
!$ will expand to the last parameter of your last line of input ... so if the package name is the same as the name of the command then that will work.

---

### Post by SoFl W on 2011-06-02
> **drs305 said:**
> Or even highlight, middle click to paste (if you have one).

That is why I love the forums, I learn something.  Didn't know about the middle click.  Thanks

---

