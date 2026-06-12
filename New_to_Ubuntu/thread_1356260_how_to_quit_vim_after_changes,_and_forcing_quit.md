---
title: "how to quit vim after changes, and forcing quit ?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-12-15
VIM is nice but if it happen that you make changes (so edit)  

then one press:
ESC ESC 

then type:
:q 

It says,... bbla bla Error you cannot quit.

How to discard changes and quit the vim  ?

---

### Post by eeperson on 2009-12-15
:q! - discard changes and quit
:wq - save changes and quit

---

### Post by Linuxforall on 2009-12-15
Type :q! and to save and exit use zz.

---

### Post by frenchn00b on 2009-12-15
thank you !!

I found this [http://www.adp-gmbh.ch/vim/short.html](http://www.adp-gmbh.ch/vim/short.html)

COuld we  start with colors "highlight-ning"? 
like 
```
vim --colors myfile.txt
```

---

