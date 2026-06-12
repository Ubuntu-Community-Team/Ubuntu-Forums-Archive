---
title: "Splash Screen Question"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-01-16
i have a two question with the splash screen. 
[LIST=1]
[*]what's a cool usplash to use?
[*]how do you show the text on the splash screen? i want to see the nice picture and loading bar but have the text below this. i had this at some point but dont remember how to get it.
[/LIST]
all help is greatly appreciated!

---

### Post by fubbleskag on 2009-01-17
i could be wrong (and if i am, someone will point it out very shortly) but i believe this is achieved by removing "quiet" from your kernel options in grub (by editing /boot/grub/menu.lst)

---

### Post by 73ckn797 on 2009-01-17
> **mjheagle8 said:**
> i have a two question with the splash screen. 
[LIST=1]
[*]what's a cool usplash to use?
[*]how do you show the text on the splash screen? i want to see the nice picture and loading bar but have the text below this. i had this at some point but dont remember how to get it.
[/LIST]
all help is greatly appreciated!

Cool is a relative term. It is only what ***you*** like.

I do not fully understand your second point. Are you referring to the initial boot screen/loading status bar?

---

### Post by 73ckn797 on 2009-01-17
> **fubbleskag said:**
> i could be wrong (and if i am, someone will point it out very shortly) but i believe this is achieved by removing "quiet" from your kernel options in grub (by editing /boot/grub/menu.lst)


I just might try removing the "quiet" from the grub and see what happens. I believe a simple "#" would suffice to comment out the entry?

---

