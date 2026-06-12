---
title: "[SOLVED] No Menus on Bootup!  Help please!"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by MickSulley on 2008-12-30
Hi,

I have already posted this on the 64 bit forum, but I am not sure that it is a 64 bit issue, so can anyone else help please?

I am running 64 bit 8.10, kernel 2.6.27-9.generic

Up yesterday everything was fine, today when I boot up it all seems OK, but I do not get the panels top and bottom with the menus, status etc. I see the normal desktop with the few icons that I normally see, but nothing at all at top or bottom.

What can I do?? It boots fine from live CD

With no menu I cannot do anything! Help please!

---

### Post by Sealbhach on 2008-12-30
Hi, try this:

```
sudo apt-get install gnome-panel
```

Then logout and log back in.


.

---

### Post by swamytk on 2008-12-30
Press Alt+F2, you will get "Run" dialog box.
Type "gnome-terminal"
In terminal window, run "killall gnome-panel"
Wait for a moment, you should get gnome panels.
If it is shown, just logout and login back.
Let us see how it behaves.

---

### Post by MickSulley on 2008-12-30
Alt F2 does not work and I cannot get to a terminal window because I have no menus.

Are there any other ways to get to either of these?

---

### Post by Sealbhach on 2008-12-30
Ctrl+Alt+F1 or F2 will bring you into another screen, you can do the commands that way. To get back just Ctrl+Alt+F1 or F2 again.


.

---

### Post by MickSulley on 2008-12-30
Thank you both so much, I am now up and running again!!!

Have you any idea what could have caused this?  As far as I know I shut down normally on Sunday and then on Monday I had this problem.

Thanks

Mick

---

### Post by Sealbhach on 2008-12-30
Glad it's all working again. 

I don't know what the cause is, maybe you removed some package and it removed the gnome panel as well. 

It happened to me once as well and I got very alarmed because I couldn't so anything.:D


.

---

### Post by MickSulley on 2008-12-31
Found it!  I did a complete removal of Evolution and all associated bits to try to fix a problem, evolution-data-server-common removes gnome-panel amongst other things.

I feel much better now I know how it happened.

Thanks for your help

---

