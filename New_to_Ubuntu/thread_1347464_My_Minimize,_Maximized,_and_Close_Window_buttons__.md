---
title: "My Minimize, Maximized, and Close Window buttons  missing"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by jbalazs on 2009-12-06
how can I get it back ??? 
Thanks

---

### Post by asmeetkumar on 2009-12-06
> **jbalazs said:**
> how can I get it back ??? 
Thanks

well its difficult to guess whats happening at your system... so please elaborate

in case you've just enabled compiz and it crashed you can do : Alt + F2

then type in : metacity --replace 
hit enter and it might return to normal

---

### Post by jbalazs on 2009-12-06
> **asmeetkumar said:**
> well its difficult to guess whats happening at your system... so please elaborate

in case you've just enabled compiz and it crashed you can do : Alt + F2

then type in : metacity --replace 
hit enter and it might return to normal

Metacity no help
The upper portion of all windows the brown stripe is missing,but when I grab
the window with Alt. left mouse it will minimize and the brow stripe is there with the all the buttons 

Any help ??

---

### Post by 5nak3 on 2009-12-06
try this:

Open up the software center / add/remove programs

Download compiz fusion icon

Go to Applications -> System tools -> Compiz fusion icon

Once you have clicked the icon a compiz square should appear in your upper taskbar.

Right click that icon and select "reload window manager".

If that still doesn't work right click it again and select "select window manager" and choose either compiz or metacity. (I know you mentioned metacity --replace didn't help but worth another shot).

---

### Post by putu.sundika on 2009-12-06
hi there, i'm beginner with ubuntu.
well, my problem nearly same.

But solved, when i'm trying using System - Preference - CompizConfig Seting Manager
(on Window Management)

-regards-

---

### Post by jbalazs on 2009-12-06
> **5nak3 said:**
> try this:

Open up the software center / add/remove programs

Download compiz fusion icon

Go to Applications -> System tools -> Compiz fusion icon

Once you have clicked the icon a compiz square should appear in your upper taskbar.

Right click that icon and select "reload window manager".

If that still doesn't work right click it again and select "select window manager" and choose either compiz or metacity. (I know you mentioned metacity --replace didn't help but worth another shot).
Thanks for the help but it's not working

---

### Post by jbalazs on 2009-12-06
> **putu.sundika said:**
> hi there, i'm beginner with ubuntu.
well, my problem nearly same.

But solved, when i'm trying using System - Preference - CompizConfig Seting Manager
(on Window Management)

-regards-

But how did you solved it?? What did you do in Window Management

Thanks

---

### Post by bumanie on 2009-12-06
Try hitting F11 with firefox open, the buttons should reappear. When they do, drag your window size so that it is smaller - it is likely you have the unmaximised window size too large. Hope this helps - happened to me once and I think that is how I fixed it - it was a while ago, so my memory may not be correct.
PS: If you have compiz running, that could be causing the problem to fix > metacity --replace in terminal

---

### Post by Elfy on 2009-12-06
> **jbalazs said:**
> But how did you solved it?? What did you do in Window Management

Thanks
If it's not what bumanie said try making sure that Window Decoration is enabled in the Effects section of the compiz settings manager

---

### Post by putu.sundika on 2009-12-06
> **jbalazs said:**
> But how did you solved it?? What did you do in Window Management

Thanks

(since I'm beginner) I just try one by one option, but that solved my problem which is can't resizing(etc) at all.

but, have you try this :
1. open your terminal
2. type gconf-editor
3. find on /apps/metacity/general/button_layout
4. you should see its value = menu:minimize,maximize,close 
5. If not, trying added.

sorry if not helping

---

### Post by Upkeep on 2010-01-31
If by any chance you've landed there by having a play with the netbook remix (like me) try:

1. terminal
2. type gconf-editor
3. navigate to /apps/maximus

Make sure the "undecorate" checkbox is empty.

Cheers
Upkeep

---

### Post by capitalfear on 2010-06-28
thanks thats what did it for me...thanks alot

---

