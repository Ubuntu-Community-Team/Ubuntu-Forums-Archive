---
title: "change the location of the exit, minimize and maximize buttons"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by computerguts on 2010-04-25
I am running ubuntu 10.04 and the first thing I noticed when I installed ubuntu 10.04 was that the exit, minimize and maximize buttons were on the left side of the windows instead of the right like they normally are in most operating systems. How could I change this. It's not really much of a problem but just a minor annoyance. 

Thanks

---

### Post by mcoleman44 on 2010-04-25
```
gksudo gconf -editor
```
apps>metacity>general>button layout
right click, edit key and change it to this:
:maximize,minimize,close

---

### Post by JCollierDavis on 2010-04-25
> **mcoleman44 said:**
> ```
gksudo gconf -editor
```
apps>metacity>general>button layout
right click, edit key and change it to this:
:maximize,minimize,close

Remember how to do this, you'll likely have to do it more than once.  When you change themes or other stuff it'll go back.

---

### Post by computerguts on 2010-04-25
thanks

---

### Post by sisco311 on 2010-04-25
> **computerguts said:**
> I am running ubuntu 10.04 and the first thing I noticed when I installed ubuntu 10.04 was that the exit, minimize and maximize buttons were on the left side of the windows instead of the right like they normally are in most operating systems. How could I change this. It's not really much of a problem but just a minor annoyance. 

Thanks

Open a terminal and run:
```
gconftool-2 --type string --set /apps/metacity/general/button_layout ":minimize,maximize,close"
```



or press Alt+F2 and run:

```
gconf-editor
```

go to /apps/metacity/general/ and set the button_layout key's value to *:minimize,maximize,close*

---

### Post by computerguts on 2010-04-25
thanks, the other command did not work let me check and see if this one works.

---

### Post by computerguts on 2010-04-25
thanks, it worked

---

