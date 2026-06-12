---
title: "Windows have no borders, toolbar gone"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by roololing on 2011-06-09
I was messing with the Compiz stuff and at one point all of my windows' borders went away. So there are no titles and no minimize/maximize/close buttons. Also, the toolbar at the top of my screen is gone. I can't move any windows or anything. Is this a common problem? How do I fix it?

---

### Post by DarkDancer on 2011-06-09
Um, try Alt-f2 then type "emerald --replace"   (No quotes of course"

Or um, shoot, what's the name of the other window manager thing?

---

### Post by DarkDancer on 2011-06-09
Oh hey, are you running Unity? Maybe someone else should answer this, sorry....

---

### Post by jtarin on 2011-06-09
Unity...I abstain too.

---

### Post by DarkDancer on 2011-06-09
If it's unity, try "unity --reset"     (once again no quotes) ;)

---

### Post by roololing on 2011-06-09
Thanks, unity reset worked. But the borders go away again if I try to enable the desktop cube, which unity can't run on.

EDIT: Okay turns out if I change anything at all with Compiz the toolbar will go away.

---

### Post by comput99 on 2011-06-09
Yeah, unity is a bitch like that sometimes.  In compiz, make sure the title bar info is checked off (under the utility category). I use to have this problem, and I started running Ubuntu Classic.  To do this, at the bottom of the login screen, there's a menu bar.  Click on the Ubuntu tab, choose Ubuntu classic from the dropdown, and then login like you normally do.  I haven't had a problem with the window title bars since.

---

### Post by wildmanne39 on 2011-06-09
> **roololing said:**
> Thanks, unity reset worked. But the borders go away again if I try to enable the desktop cube, which unity can't run on.

EDIT: Okay turns out if I change anything at all with Compiz the toolbar will go away.
Hi, follow this guide and unity can run the cube I have an amazing cube with effects in natty. After you have follow this guide and you go to  set up more effects you will miss up windows again just log out and back in to fix it each time until you are done with changing settings.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by hakermania on 2011-06-09
I'd like to add that by just running
```
gtk-window-decorator
```
windows' borders will come back

---

### Post by roololing on 2011-06-19
That worked, wildmanne39. Thanks a ton.:D

---

### Post by wildmanne39 on 2011-06-19
> **roololing said:**
> That worked, wildmanne39. Thanks a ton.:DHi, your welcome enjoy the cube and effects, and if you change settings you might want to do it one at a time in case you make your system respond slow you will know what setting to change back. Would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by tomcatification on 2011-06-19
all i did was restart linux

---

### Post by pritam_par on 2011-08-10
I too faced the same problem, just enabling the **window Move** and **Window Decoration** in compiz setting manager has solved the problem

---

