---
title: "wiped out panel!"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by shallowthought on 2010-09-16
How's this for smarts?
I accidentally wiped out the entire panel at the top of the screen.
Gone are:   

Applications  Places System                                  

and on the right side also gone is the button to shut down, etc.

How do I get them back?

Real clever, right?

---

### Post by Rubi1200 on 2010-09-16
Here is a fix, but be warned this will reset any custom settings you had before:
Run the commands in the terminal (Applications > Accessories)

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel 
pkill gnome-panel
```

---

### Post by shallowthought on 2010-09-16
> **Rubi1200 said:**
> Here is a fix, but be warned this will reset any custom settings you had before:
Run the commands in the terminal (Applications > Accessories)

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel 
pkill gnome-panel
```

Thanks for the reply, but ...  I don't know how to get to terminal since I don't know how to get to
Applications without the panel!

---

### Post by Rubi1200 on 2010-09-16
> **shallowthought said:**
> Thanks for the reply, but ...  I don't know how to get to terminal since I don't know how to get to
Applications without the panel!
Oops sorry! :oops:

Alt + F2 and type in gnome-terminal

---

### Post by shallowthought on 2010-09-16
It worked! Thanks so much!
You made my day.
I think I need to remember how to do this!

---

### Post by Rubi1200 on 2010-09-16
You are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

> I think I need to remember how to do this! 	
Write it down somewhere perhaps?

---

