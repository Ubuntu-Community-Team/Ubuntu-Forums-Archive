---
title: "Firefox, searchbar, adblock not working."
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Crunchy the Headcrab on 2009-06-18
Jaunty x64

Hey all.  Everything was working fine until ubuntu updated a few moments ago.  Now I can't use the search bar on firefox, it's there but there is no way to send and it thinks that I don't have any search providers installed.  I typically use Google.  It wouldn't let me add any providers, it just sits there and does nothing when I try.  I have to close the dialog box for adding search providers by hitting the X because hitting OK or CANCEL does nothing.

Also Adblock Plus is not working now.  It doesn't appear in it's space next to the searchbar.  It says it is still installed, so I tried disabling it and re-enabling it.  No dice.  Then I tried uninstalling it and reinstalling.  It says it will be uninstalled next time firefox is started, but instead a popup comes up that says a new add-on has been installed and wouldn't you know it, it is Adblock plus.  Still not working, can't be uninstalled.

Restarting the system doesn't help.

EDIT: ****. It appears the address bar isn't working either.

EDIT 2: [COLOR=Red]Nevermind.  Fixed.  Cause I'm the Shiz :p
Tip: Deleted user preferences in my home folder > .mozilla
[/COLOR]

---

### Post by lovinglinux on 2009-06-18
> **Crunchy the Headcrab said:**
> Tip: Deleted user preferences in my home folder > .mozilla

You don't have to delete the entire .mozilla folder, specially if you want to preserve settings and extensions. These problems are usually related to the corruption of two files on your profile: *places.sqlite* and *localstore.rdf*. The first one cause issues with bookmarks and address bar, the second cause issues with toolbars and extensions. Deleting these files would fix each problem.

---

