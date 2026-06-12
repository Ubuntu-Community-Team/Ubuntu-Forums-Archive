---
title: "Conky startup issue."
date: 2009-09-26
forum: New to Ubuntu
---

### Post by skymera on 2009-09-26
Hello ! 

I've got my Conkty set up niiiice, and i added it to my sessions and it loads when i start ubuntu :KS

But it seems to load on top of the desktop, like a window. It sits above everything else? (Firefox etc.)

However, if i kill conky and start it manually with Alt+F2 it sits in the desktop background.

How do i get Conky to load in the desktop background like it's supposed to?

---

### Post by wojox on 2009-09-26
What the top (config) part of .conkyrc look like?

---

### Post by scheibo on 2009-09-26
I could be wrong, but if conky loads before gnome does, it will place itself on top of everything. iirc, the fix for this is to throw a "sleep <x> && conky" into your startup script, where <x> is a certain amount of seconds, as this gives your window environment enough time to startup. i think when i had conky i use "sleep 10 && conky".

---

### Post by skymera on 2009-09-27
Thank you :D

I'll try tomorrow, wrapped up in college and getting 2 different laptops running Ubuntu.

---

