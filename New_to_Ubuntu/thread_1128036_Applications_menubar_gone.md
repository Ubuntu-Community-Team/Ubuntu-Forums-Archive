---
title: "Applications menubar gone"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Elegia on 2009-04-17
I think I accidentally pressed some key combination yesterday and now in many applications the menubars have disappeared, like in Evolution, Eclipse and Exaile. How can I get them back? 

In case it helps, I'm working with Gnome and also installed Gnome-do yesterday, but I don't think the problem is related to that.

---

### Post by lisati on 2009-04-17
IF the menu bar is still showing, you can right-click on it and select "add to panel". This will then give you choices about what to show.

---

### Post by Elegia on 2009-04-17
I assume you're talking about the gnome panels at the top and bottom of the screen? That's not what I meant I'm afraid. I mean the actual menubar in any application, the bars that say 'File, 'Edit', 'Extra', ... That's what I no longer see.

---

### Post by reeseslover531 on 2009-04-17
if you are running compiz sometimes, that happens run 
```
compiz --replace
``` 
and that sometimes helps.

---

### Post by Elegia on 2009-04-17
Thanks. I tried it but unfortunately it has no effect :(. I also tried running things without compiz, but that doesn't work either.

Edit: SOLVED. I found an older thread on these forums about the same problem. Uninstalling the package 'libglobalmenu-gnome' (and possibly all other globalmenu packages) restored all menubars. :)

Thanks for all the help.

---

