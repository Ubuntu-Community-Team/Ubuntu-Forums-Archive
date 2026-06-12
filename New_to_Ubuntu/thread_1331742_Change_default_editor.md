---
title: "Change default editor"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by freesitebuilder on 2009-11-19
I'm running 9.04 (Jaunty) - I plan to upgrade after a hardware upgrade in a few days.

I want to change the default editor from gedit to Geany  but the only info I can find  here and in the documentation is dated from 2005 to 2007, and I'm reluctant to try it on a later version of Ubuntu as I don't really know if there are any differences that will affect the instructions given, and how to put it right if necessary.

I've tried right-clicking a file, choosing "open with other app" and then choosing Geany, but although it opens OK, after I close it, re-opening it uses gedit again. And although the dialog box says "open all plain text files with ..." that doesn't happen - any other txt files open in gedit.

Can anyone point me to the current instructions?

TIA

---

### Post by ibuclaw on 2009-11-19
There is a defaults.list inside /etc/gnome.

If you copy that to your profile directory.

ie:
```
cp /etc/gnome/defaults.list ~/.local/share/applications
```
Then change all "gedit" to "geany"
```
sed -i 's/gedit/geany/' ~/.local/share/applications/defaults.list
```
Job done!

Any information in that will be overrided by the mimecache.list file stored in the same profile directory, if I recall correctly.

Regards
Iain

---

