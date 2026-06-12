---
title: "GTK, Metacity, Gnome and Nautilus"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by icyest on 2008-12-26
What's the difference between GTK, Metacity, Gnome, and Nautilus? 
I keep hearing them interchangeably. 
Coming from a Windows XP world, I only know of the Explorer program. Are these 4 synonymous components of one big entity?

---

### Post by RomeReactor on 2008-12-26
Hi. GTK is the Gnome Tool Kit, used to create the graphical interfaces. Metacity is the display manager; Gnome is the desktop (as opposed to XFCE or KDE), and Nautilus is the file browser.

---

### Post by icyest on 2008-12-26
Where can I access this Gnome Tool Kit? I have not seen it before. I recall we used to be able to make vista-like themes back in ubuntu 7. Is this the graphical editing settings/tools that you're talking about?

---

### Post by mc4100 on 2008-12-26
> **icyest said:**
> Where can I access this Gnome Tool Kit? I have not seen it before. I recall we used to be able to make vista-like themes back in ubuntu 7. Is this the graphical editing settings/tools that you're talking about?

Theming the UI can be done with the "Appearance" capplet. It's found under System -> Preferences -> Appearance. 
Ready-made themes can be downloaded from [here]("http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=100"). Try mixing and matching, via the customise button, for a more personalised result.


> What's the difference between GTK, Metacity, Gnome, and Nautilus?
An easy way to think of it is this:
The buttons and handles, on the top of the windows, which you use to do things like minimisation, are handled by *metacity*.
The stuff **inside** those windows, like scrollbars, text-fields and buttons, are GTK.
Nautilus is a file manager, it open when you double click a folder.
And [GNOME]("http://www.gnome.org") is the project which brings all the bits together to create a useable desktop.

---

### Post by RomeReactor on 2008-12-26
GTK is the set of bits and pieces used to create the interfaces; to actually make a GUI I think you can use Entity or Glade. Both are available in the repositories. Making a theme for Gnome is different.

---

### Post by albinootje on 2008-12-26
> **RomeReactor said:**
> Hi. GTK is the Gnome Tool Kit, used to create the graphical interfaces. Metacity is the display manager; Gnome is the desktop (as opposed to XFCE or KDE), and Nautilus is the file browser.

GTK = Gimp Tool Kit. 
The Gnome project started using it to build the Gnome Desktop.
 
[http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B)
[http://www.gtk.org/](http://www.gtk.org/)

---

### Post by mc4100 on 2008-12-26
> **albinootje said:**
> GTK = Gimp Tool Kit. 
The Gnome project started using it to build the Gnome Desktop.
 
[http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B)
[http://www.gtk.org/](http://www.gtk.org/)

:) Well... if we're going to nitpick:

GTK = Good to know.

GTK+ = GIMP Tool Kit.

---

### Post by DJ_Peng on 2008-12-26
> **mc4100 said:**
> An easy way to think of it is this:
The buttons and handles, on the top of the windows, which you use to do things like minimisation, are handled by *metacity*.
The stuff **inside** those windows, like scrollbars, text-fields and buttons, are GTK.
Nautilus is a file manager, it open when you double click a folder.
And [GNOME]("http://www.gnome.org") is the project which brings all the bits together to create a useable desktop.
I've never heard it put so succinctly. I'm going to have to subscribed to this thread just so I have that so I can have it on my hard drive. Thanks!

---

### Post by mc4100 on 2008-12-26
> **DJ_Peng said:**
> I've never heard it put so succinctly. I'm going to have to subscribed to this thread just so I have that so I can have it on my hard drive. Thanks!
Thanks.

But to be a little less succinct:
Metacity does more than just handling decorations, and the window management that I hinted it (no pun intended) ... e.g., compositing. Even then, they mightn't even be using it: perhaps emerald, along with compiz.
Of course, just because a window has appeared, doesn't mean it must be using GTK+
(Chances are if it's got a "K" in there somewhere, it'll be using QT, so it won't match the user's theme settings.)
And while an application like Firefox (and to a certain extent OO.o apps) appear to look themed, they aren't true GTK+ widgets -- firefox will skin it's XUL elements with CSS to match the theme. Not terribly important, but it does have a big impact on Desktop Integration.

... but Nautilus, I'm sure, is just a plain old file manager ... sort of.
;)

(EDIT: I use 'and' waaaaaaaay too much: Fixed, for now)

---

### Post by RomeReactor on 2008-12-26
> **albinootje said:**
> GTK = Gimp Tool Kit. 
The Gnome project started using it to build the Gnome Desktop.
 
[http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B)
[http://www.gtk.org/](http://www.gtk.org/)

That's what happens when I post half-asleep. :tongue:

Also, Metacity is a *window* manager, not a display manager. #-o

---

