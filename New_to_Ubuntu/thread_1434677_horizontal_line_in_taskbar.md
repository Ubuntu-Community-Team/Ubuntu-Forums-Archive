---
title: "horizontal line in taskbar"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by infestor on 2010-03-20
i use my taskbar at 40 px size but regardless the theme i use i always get this horizontal line.
is there a way to fix this?

---

### Post by chaanakya_chiraag on 2010-03-20
The background you are using (for the taskbar) is too small (height-wise).  Try resizing it in GIMP or something.  That should work out :)

---

### Post by infestor on 2010-03-21
but it is the theme's background. so i have to find that image file and edit it?

---

### Post by mechro on 2010-03-21
Try alt+F2 and run gconf-editor. Navigate to **apps > panel > toplevels > top_panel_screen0 > background**: check the **fit** box.

---

### Post by chaanakya_chiraag on 2010-03-21
For future reference, it's the one set in right-click (**on the panel**)-> Preferences -> Third Tab ->Background.

---

### Post by infestor on 2010-03-22
> **mechro said:**
> Try alt+F2 and run gconf-editor. Navigate to **apps > panel > toplevels > top_panel_screen0 > background**: check the **fit** box.

i did that and booted the system but does not help.

---

### Post by chaanakya_chiraag on 2010-03-22
Have you saved the file you are using for the background of the **panel**?  If you have, edit its height and you should be good to go.  If not, redownload it (**saving it this time!**) and edit it.  Then, follow my instructions above to set the background of the panel.

---

### Post by infestor on 2010-03-26
i dont know which file is used in elementary-theme :(
it should be under /usr/share/themes/elementary

---

### Post by chaanakya_chiraag on 2010-03-26
Wait, so the *theme* is setting the background.  I'm not on my Linux box right now, but I'll take a look around and see if I can find what the file should be called :)

---

### Post by mechro on 2010-03-26
> **infestor said:**
> i dont know which file is used in elementary-theme :(
it should be under /usr/share/themes/elementary

Can you post a link to where you got this theme?

---

### Post by infestor on 2010-03-27
> **mechro said:**
> Can you post a link to where you got this theme?

[https://launchpad.net/~elementaryart/+archive/ppa](https://launchpad.net/~elementaryart/+archive/ppa)

---

### Post by mechro on 2010-03-27
> **infestor said:**
> [https://launchpad.net/~elementaryart/+archive/ppa](https://launchpad.net/~elementaryart/+archive/ppa)

OK. I've downloaded the theme and reproduced your problem...

[IMG]http://i39.tinypic.com/2wejrip.jpg[/IMG]

In a previous post I said "... alt+F2 and run gconf-editor. Navigate to **apps > panel > toplevels > top_panel_screen0 > background**: check the **fit** box". I did this and here is the result...

[IMG]http://i39.tinypic.com/21ox26g.jpg[/IMG]

Have you got **gconf-editor** installed? Do you have a **top_panel_screen0**?

---

### Post by infestor on 2010-03-28
> **mechro said:**
> OK. I've downloaded the theme and reproduced your problem...

[IMG]http://i39.tinypic.com/2wejrip.jpg[/IMG]

In a previous post I said "... alt+F2 and run gconf-editor. Navigate to **apps > panel > toplevels > top_panel_screen0 > background**: check the **fit** box". I did this and here is the result...

[IMG]http://i39.tinypic.com/21ox26g.jpg[/IMG]

Have you got **gconf-editor** installed? Do you have a **top_panel_screen0**?

i had already done that but *strangely* it doesn't change anything!

---

### Post by mechro on 2010-03-28
> **infestor said:**
> i had already done that but *strangely* it doesn't change anything!

OK. You should find the panel image here...

**/usr/share/themes/elementary/gtk-2.0/Panel/panel.png**

You'll need to be root to edit it so do **gksudo nautilus** and navigate to the image.

It's 24 pixels high so you could scale it to 40 pixels high in Gimp.

---

### Post by infestor on 2010-04-16
> **mechro said:**
> OK. You should find the panel image here...

**/usr/share/themes/elementary/gtk-2.0/Panel/panel.png**

You'll need to be root to edit it so do **gksudo nautilus** and navigate to the image.

It's 24 pixels high so you could scale it to 40 pixels high in Gimp.

thanks a lot!:guitar:

---

