---
title: "How to change key bindings in Evince?"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by wolfmanmi on 2011-04-24
Hi all.  I am just setting up Ubuntu and would like to change/add some key bindings in the native pdf viewer.  Specifically, I would like to use ALT + arrow to return to the previously viewed page.  At the moment, I just click the Back button in the toolbar.

Ultimately, it would be nice to know how to edit key bindings for any program.  Any suggestions?

---

### Post by Locke_99GS on 2011-04-24
Try **System -> Preferences -> Keyboard Shortcuts** and see if what you want to do can be done there.

Try to be wearing that the key bindings there (x) don't interfere with any you might use for Compiz,

---

### Post by wolfmanmi on 2011-04-24
Thanks for the quick reply.  I think that will just edit global, i.e., system, shortcuts.  Am I wrong?  I am just wanting to edit application specific shortcuts.

---

### Post by Locke_99GS on 2011-04-24
I learned something looking for this. :p I just tried this, and it works exactly as advertised.

[http://library.gnome.org/users/evince/stable/shortcuts.html.en](http://library.gnome.org/users/evince/stable/shortcuts.html.en)

---

### Post by wolfmanmi on 2011-04-24
Nice suggestion!  Unfortunately, it's not working for my needs.  I would like to use ALT + {left arrow} to go back, the standard keyboard shortcut for web browsers and in the pdf viewers Sumatra and Adobe Reader.

I am not sure if the problem is that I am hovering over an item in the toolbar (and not a menu item) or if it is because I want to use ALT + (whatever).

---

### Post by Locke_99GS on 2011-04-24
You have to open the "Go" menu in when Evince is open, and put the mouse over "Previous Page" and hit the new key-combo (when that option is checked in gconf) then do the same for "Next Page". Then uncheck the option in gconf, and it's set.

I set mine earlier to Alt-Left and Alt-Right using the method described in the article.

---

### Post by wolfmanmi on 2011-04-24
I am trying to bind a key for the "Back" button.  This jumps back to the previously viewed page, as opposed to the "previous page" which is the current page number minus one.

The back feature is not listed in the Go menu.

---

### Post by llamabr on 2011-04-24
i use xpdf, which you can quickly install from the repos.  It has several nice keybindings that I like:

p to go to the previous page
n to go to the next page
h to fit the doc to the height of the window
w to fit the doc to the width of the window

and a few others.  I don't care much for evince.  When I can't get xpdf, I try to use gv.

---

### Post by lavankohsa on 2012-01-08
Hi,

I am trying to change key bindings for evince in ubuntu 11.10 as they shown on their website but i am not able to do that. i want for right arrow key for next page and left arrow key for previous page.

---

