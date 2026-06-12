---
title: "/etc/default/grub: 33: Syntax error: EOF in backquote substitution ;error please help"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by migs73 on 2011-04-23
Hey all

I was following the guide for sorting my poor resolution on plymouth ([http://jechem.blogspot.com/2011/04/fix-plymouth-splash-screen-in-ubuntu-on.html](http://jechem.blogspot.com/2011/04/fix-plymouth-splash-screen-in-ubuntu-on.html)) when I follow the instructions I get this error when trying to update grub
```
/etc/default/grub: 33: Syntax error: EOF in backquote substitution
```
I think it is because the guide says to alter the grub file with the following lines;
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
```

Which I (now) notice is minus a set of quote marks.

Any body out there know if this is the problem, and if so where do I put the " ??

Hope someone can help.

Mike

---

### Post by migs73 on 2011-04-23
Solved

I found the answer elsewhere. The quotes go at the end of the line.

Thanks for looking.

Mike

---

### Post by ranger1021994 on 2011-08-13
> **migs73 said:**
> Solved

I found the answer elsewhere. The quotes go at the end of the line.

Thanks for looking.

Mike

Thanks  :):)
+1 It worked for me

---

