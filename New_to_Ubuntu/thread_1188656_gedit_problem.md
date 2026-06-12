---
title: "gedit problem"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2009-06-15
I haven't been able to get any response on the following in General Help, so maybe that's their way of telling me I've been in the wrong forum?

In the months that I have been using Ubuntu (still at 8.04 for now), there have been instances of things needing some tweaking to get working, but nothing has broken.

Suddenly my gedit stopped printing across the network (Samsung printer is connected to a Windows XP machine) although it prints fine from Open Office 2.0. Today when I attempted to do a print preview, gedit froze trying to prepare the preview.

I can open/edit/close a new tab of gedit, and can minimize/maximize the window, but cannot close the frozen tab without resorting to System Monitor > Processes Tab > End Process.

Why it is behaving this way?

Should I just reinstall gedit?

---

### Post by mjpatey on 2009-06-15
That's what I'd try first.  Go to Synaptic and tell it to "remove completely" (which removes setting, config files, etc.)... make sure to hit "Apply" before closing Synaptic.

Then sudo apt-get install gedit to reinstall.  Hope this helps!

-Mark

---

### Post by mdgrech on 2009-06-16
also b4 you reinstall it make sure all of your gedit config files have been deleted w/ this command:

rm -rf ~/.gnome2/gedit

---

### Post by Odyssey1942 on 2009-06-16
Thanks Mark and MD,

When I open Synaptic and mark gedit for removal a pop-up shows and says "The chosen action also affects other packages. The following changes are required in order to proceed" and shows 

"To be removed:
Ubuntu-desktop"

and offers a choice of "Cancel" or "Mark" (for removal)

This makes me nervous. Am I opening a can of worms if I remove the desktop? Does this mean that any files or folders now on my desktop will be deleted?

Also in Synaptic there are two gedits

one is "gedit"

the other is "gedit-common"

Should both be removed?

Also the marking options are:

Mark for Reinstallation
Mark for Removal
Mark for Complete Removal

From your posts, I assume that I should not pick the "Reinstallation" option, rather one of the two Removal options. What is the difference between the two?


Or might "Mark for Reinstallation" be the better choice considering that it does not indicate that the Desktop will be removed?

---

### Post by Celauran on 2009-06-16
Ubuntu-desktop is a meta package and can be safely removed. I'd purge both gedit and gedit-common. Clean up any residual config files, then reinstall ubuntu-desktop at the same time you reinstall gedit.

When removing them via Synaptic, I'd mark them for complete removal. This, in theory, also removes all associated config files (not so much in practice, but you're going to do that afterwards anyways).

---

### Post by Odyssey1942 on 2009-06-16
Thanks Celauran,

Will the files and folders now on my desktop will be deleted if the Desktop is removed then reinstalled?

If so, what is the expeditious way to move them so that they can be moved back after all of the removals and reinstallations?

Also, the comments in the lower pane in Synaptic for ubuntu-desktop says:

"The Ubuntu desktop system 
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed."

I hope my inexperience is not too obvious here, but I trust that the last line above means permanently and would not apply to a removal/reinstallation?

---

### Post by Celauran on 2009-06-16
Removing ubuntu-desktop won't actually remove your desktop. The package itself doesn't actually contain anything; it's just a list of other packages. This way, to install the GNOME desktop, you can simply tell it to install ubuntu-desktop rather than the 75000 packages that actually make up GNOME.

---

### Post by Mornedhel on 2009-06-16
> **Odyssey1942 said:**
> Will the files and folders now on my desktop will be deleted if the Desktop is removed then reinstalled?

Here "desktop" refers to "a desktop installation" as opposed to a server. The ubuntu-desktop package is used only to depend on the individual packages that compose the Gnome desktop *environment* as installed by Ubuntu. The reverse is not true : nothing depends on ubuntu-desktop and nothing (no files, packages, programs, etc) will be removed once the ubuntu-desktop package is removed. Your files are safe and will not be removed.

> **Odyssey1942 said:**
>  Also, the comments in the lower pane in Synaptic for ubuntu-desktop says:

"The Ubuntu desktop system 
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed."

I hope my inexperience is not too obvious here, but I trust that the last line above means permanently and would not apply to a removal/reinstallation?

The description is a bit misleading. Proper upgrades still occur as long as you are not trying to upgrade from a version of Ubuntu to another. Systems where the ubuntu-desktop package are removed (for instance mine) are still updated/upgraded normally and no functionality whatsoever is lost.

---

### Post by Odyssey1942 on 2009-06-16
So, if I understand this correctly, when I remove and reinstall the Desktop, all my folders and files will show up on the desktop without my having to remove them before and replace them after the re-installation of the desktop?

It also just occurred to me that the "Desktop" might be somehow related to the GUI. When it is time to reinstall the desktop, the Synaptic will still be there, yes?

---

### Post by mjpatey on 2009-06-16
Odyssey,

Yes, it's fine to remove ubuntu-desktop.  Your Desktop will not go away, all your programs will be intact.  "ubuntu-desktop" is simply a container with a list of packages to all install/upgrade at once when appropriate.  You can remove it for weeks, months at a time, and life will still be good.  :-)  When you re-install it (it's a tiny file), you'll soon see the list of packages that underwent upgrades while ubuntu-desktop was absent.  Allow them to upgrade as usual, and you're fine.

You'll only be uninstalling it for a few seconds / minutes, so you probably won't even have to go through that.

---

### Post by Odyssey1942 on 2009-06-16
Many thanks to all for the valuable guidance.

---

### Post by mjpatey on 2009-06-16
You're welcome.  Post back with your results!

---

### Post by dilaudid on 2010-11-24
Hi, I had a problem with gedit not printing (no job submitted, gedit just flickers and returns to the document - also print preview doesn't happen - gedit just returns to the doc), I found rather than uninstall I just renamed the gedit print settings file:
```
mv .gnome2/gedit/gedit-print-settings .gnome2/gedit/gedit-print-settings2
```
gedit hasn't recreated the gedit-print-settings file, but now printing works fine in gedit.

I've attached the settings file for info.

---

