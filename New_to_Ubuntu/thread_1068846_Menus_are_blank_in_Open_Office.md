---
title: "Menus are blank in Open Office"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by jackfear on 2009-02-13
I am new to Ubuntu and have just installed 8.10.  I have installed the
Kubuntu desktop as well.

When I load Open Office word processing, all the menu items (File,
Insert, Edit, Tools etc) are missing as are the contents of the pull
down menus.

This problem also occurs in Kile (a LaTeX  editor), K3b, Amarok and
Muse where the top menu items are OK but the pull down menus are
blank.

I believe I must be missing a library item somewhere (A piece of Qt
perhaps?) but I don't know how to check this.  I would hate to
reinstall the whole system.

Another clue?  I loaded the Xubuntu desktop and the menus all show up
correctly in this mode!

Any suggestions would be much appreciated.

Best,
        Jack

---

### Post by jou770d on 2009-02-13
Maybe because of a custom theme?
Are the menus empty as in no text or items? If you clicked blindly in the menu, does anything happen?

---

### Post by ajgreeny on 2009-02-13
If you are running a 3d desktop with compiz enabled, try running without it and see if it helps. ```
metacity --replace
``` should stop compiz, and ```
compiz --replace
``` start it again if you want.

It may simply be a conflict between your theme, and one or more of the compiz plugins you have enabled so try different combinations of those as well, if you want compiz running on your system.

---

### Post by binbash on 2009-02-13
It is nvidia driver bug.Upgrade your driver to 180 or try this :

System > Preferences > Appearance > Fonts > turn on subpixel smoothing

---

### Post by jackfear on 2009-02-13
Problem solved!

Thanks ajgreeny and binbash.  Both suggestions (metacity and smoothing) worked!

Upgrading my nvidia driver was not a success.  On restart it dropped me into a basic graphics mode, so I reverted to 96.

Jack

---

### Post by jackfear on 2009-02-13
I spoke too soon!  The pixel smoothing option solved the Open Office problem but did not populate the **sub**menus of the other applications I mentioned (Kile, K3b, Amarok and Muse).

The metacity command never terminates and control C freezes the terminal window.

I have uninstalled the Kubuntu desktop but I still have the Xubuntu desktop and, as I mentioned before, all programs work correctly if I login as an Xfce session.

Jack

---

