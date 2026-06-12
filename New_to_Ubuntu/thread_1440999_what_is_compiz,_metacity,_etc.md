---
title: "what is compiz, metacity, etc???"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by zery on 2010-03-28
hi guys,

what is compiz, metacity, etc...use for? and how to really use it anyway, it's one of the gnome desktop features that i dont understand.

---

### Post by _h_ on 2010-03-28
Compiz:

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Metacity:

[https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity)



:popcorn:

---

### Post by amauk on 2010-03-28
They are both window managers

Window managers are programs that take all the running graphical applications on a system, and work out how to actually display them on the screen

They deal with the window placement and actions taken when window events are triggered (minimize, maximize, close, etc.)

X Window managers all follow a standard protocol, so they are completely interchangeable.

---

### Post by MichealH on 2010-03-28
Compiz and Metacity affect the way the windows look and run. Compiz provides some jaw-dropping effects while Metacity cn do some pretty basic ones but before you go ahead and turn "on" Compiz You need a Comaptible Card a Sis Card or a card with no 3d effects will not run Compiz but will run Metacity.

**_To enable Compiz:_**

Right Click on Desktop > Change Desktop Background > Visual Effects and then Click Normal or Extra.

**_To enable Metacity Compositing:_***[SIZE="1"](This is also a option to choose If Compiz cant enable effects)[/SIZE]*

Press ALT+F2 and the type
```
gconf-editor
```

Goto Apps> Metacity> general and then tick "compositing manager"(or something like that)

---

### Post by zery on 2010-03-29
Dear All,

Thank you for the reply, its coming to me now...

---

