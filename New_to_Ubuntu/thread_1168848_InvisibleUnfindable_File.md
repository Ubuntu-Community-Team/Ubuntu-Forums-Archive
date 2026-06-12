---
title: "Invisible/Unfindable File?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by bug67 on 2009-05-24
I have a weird problem (if you wanna call it a problem)

Here awhile back I installed Boxee, didn't like it, ran uninstall from Add/Remove.

Boxee went away but now, every time I download something and the window pops up so I can navigate to where I want to save the downloaded file, (I usually save to my desktop) there is a "Remove Boxee" file showing on my desktop.  But, if I actually look at my actual desktop, or do Places>Desktop, there *is* no such file.  What do I do?  How do I get rid of this residual/hidden/invisible/*not-actually-there* file?

---

### Post by Jive Turkey on 2009-05-24
have you tried opening the desktop directory with nautilus and selecting View>Show Hidden Files in the menu?

---

### Post by dnairb on 2009-05-24
I had an issue similar to this, in that in nautilus, items in the ~/Desktop folder did not reflect what was actually displayed on the desktop.

Try, in terminal, **ls -ah1 ~/Desktop**

---

### Post by bug67 on 2009-05-24
> **Jive Turkey said:**
> have you tried opening the desktop directory with nautilus and selecting View>Show Hidden Files in the menu?

That did it.  Thanks!:D

---

