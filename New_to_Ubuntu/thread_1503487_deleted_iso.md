---
title: "deleted iso"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by rockinroll on 2010-06-06
i was trying to make some room so i deleted old iso's and well one of them was the installation iso now when i run updates and packet mngr i get errors files missing and so on. can i copy my cd to a folder to replace them? how can i fix this ? would it be easier to just reinstall? if so how do i do that? im runnung win 7 and ubuntu 10.4 and a dual boot.  i reallly like this version of ubuntu im not completely lost.

---

### Post by halitech on 2010-06-06
just open the Package manager, go into the sources and uncheck the source where the ISO is listed. reload and the error should be gone.

---

### Post by rockinroll on 2010-06-06
i dont see what your talking about in packet mngr

---

### Post by wilee-nilee on 2010-06-07
A missing ISO sounds like wubi install or a install with a ISO loader to a thumb or HD. A little more detail is needed. If it is a install inside of windows, technically it's not a dual boot in a classic interpertation. So more info and really posting this boot script will outline your setup pretty well even if it is a wubi. On occasion people make a partition during a wubi install when it isn't needed and the script will show this so post it in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I suggest this script as it gets to the heart of the setup without continuous questions and confirmations that can be seen with the script.

---

