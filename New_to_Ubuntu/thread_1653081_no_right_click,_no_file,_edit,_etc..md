---
title: "no right click, no file, edit, etc."
date: 2010-12-26
forum: New to Ubuntu
---

### Post by dulce on 2010-12-26
everything normal yesterday. this morning i have no right click functions, neither with the mouse or the touchpad.

i also can't use file, edit, view, etc, none of those. left clicking won't do it in other words. other wise left click works.  :confused:

thanks in advance, i know you're all geniuses. i myself lack experience but am capable of learning.:D

---

### Post by dulce on 2010-12-26
keyboard shortcuts don't work either.

---

### Post by amjjawad on 2010-12-26
What version of Ubuntu are you using?
Is this Normal or Wubi Installation? did you install Ubuntu within Windows?
Did you try to reboot your machine in the process and still got the same issue?

---

### Post by dulce on 2010-12-26
[COLOR=SeaGreen]thanks for replying. answering you in green:[/COLOR]

What version of Ubuntu are you using? [COLOR=SeaGreen]10.04[/COLOR]

Is this Normal or Wubi Installation? [COLOR=SeaGreen]i assume it was normal. i didn't install it. i can ask the person who id if necessary. [/COLOR]did you install Ubuntu within Windows? [COLOR=SeaGreen]no windows[/COLOR].

Did you try to reboot your machine in the process and still got the same issue?[COLOR=SeaGreen] yes i rebooted. no change.[/COLOR]

---

### Post by karthick87 on 2010-12-26
Type this in terminal,
```
gconftool-2 --set /apps/nautilus/preferences/show_desktop --type bool 1
```

---

### Post by dulce on 2010-12-26
> **karthick87 said:**
> Type this in terminal,
```
gconftool-2 --set /apps/nautilus/preferences/show_desktop --type bool 1
```

when i type it in a terminal and press enter nothing happens, it shows my name@my name, etc again asking for a command.

---

### Post by karthick87 on 2010-12-27
Did your problem solved or still continuing??You are not able to right on Desktop or you cant able to right click any where?

---

### Post by dulce on 2010-12-27
as of this morning everything works.

thank you karthick, you're a genius, i love you and everyone in this forum. :D

can you tell me why that happened?

---

### Post by mcduck on 2010-12-27
> **dulce said:**
> as of this morning everything works.

thank you karthick, you're a genius, i love you and everyone in this forum. :D

can you tell me why that happened?

Probably because you ran the command dulce gave you. ;)

(successful commands don't usually report anything to you. If something goes wrong you get an error message, if you get no error that means the command completed without any problems.)

---

### Post by dulce on 2010-12-27
> **mcduck said:**
> Probably because you ran the command dulce gave you. ;)

(successful commands don't usually report anything to you. If something goes wrong you get an error message, if you get no error that means the command completed without any problems.)

lol, i meant why did i lose those functions to begin with but your answer is useful also to this noob.

---

