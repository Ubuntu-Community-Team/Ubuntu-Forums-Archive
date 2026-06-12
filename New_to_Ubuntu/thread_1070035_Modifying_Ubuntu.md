---
title: "Modifying Ubuntu"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by MasterProg on 2009-02-14
I need to modify Ubuntu so that a program I wrote would load automatically every time my computer is turned on. The program uses GTK and goes fullscreen by itself. How do I do that?

---

### Post by hAvAAck on 2009-02-14
Go to System -> Preferences -> Sessions and add it to startup

---

### Post by MasterProg on 2009-02-14
Yeah, I've already tried this. For some reason, the program doesn't appear on the screen and works in background.

And well, I don't even need Gnome to be loaded. It would be very nice if it was possible to get rid of it.

---

### Post by llamabr on 2009-02-14
How are you running a gtk program without running x?

gnome starts on bootup because a program called gdm is running.  If you don't need x, you can remove gdm.

What is this gtk app?

---

### Post by MasterProg on 2009-02-15
Since it's a graphical application, X server is required and *is* running. I wrote the program myself.

---

### Post by Xiong Chiamiov on 2009-02-15
In your ~/.xinitrc, add
```

program name &

```

---

### Post by MasterProg on 2009-02-15
I got it working.

But ~/.xinitrc had no effect for me. I googled it and I found out that GDM was using ~/.xsession instead. I did the same with ~/.xsession and now it works exactly as I wanted.

Thanks a lot!

---

