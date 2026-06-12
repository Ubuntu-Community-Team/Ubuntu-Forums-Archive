---
title: "Human Theme messed up after update"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by bindatype on 2008-12-11
I did an update today of you Hardy distro and now, after rebooting the Gnome Human theme is borked. Anyone else having this problem?

---

### Post by Michael.Godawski on 2008-12-12
hi bindatype, 
what do you mean with borked?

Did you try to re-install the theme:
```
sudo apt-get remove ubuntu-gdm-themes
sudo apt-get install buntu-gdm-themes
```

---

### Post by bindatype on 2008-12-12
What I should have written is there is an error message before the login screen that reads

Cannot recognize image file format for /usr/share/gdm/themes/Human/bottom_bar.svg

I click OK and I login. All the themes are gone except "custom"
errmsg (END) 

I tried removing and reinstalling ubuntu-gdm-themes and rebooted but the problem remains. It was a good idea.

---

### Post by thinking2loud on 2009-01-01
Hmm...coincidence?  This is currently happening to me.  Did you ever find a solution to this problem?

Here's another possible clue:  The menu bar of windows used to be the usual brownish series of tones commonly associated with the default with Ubuntu.  Now, it's dark blue.

And what is the .svg format?  Some sort of graphics format?  When I go to the file bottom_bar.svg, and try to open it, the Eye of Gnome starts up and it says Unrecognized File Format.  I'm guessing some library that interprets these things has got stomped on.  gtk+ ???

---

