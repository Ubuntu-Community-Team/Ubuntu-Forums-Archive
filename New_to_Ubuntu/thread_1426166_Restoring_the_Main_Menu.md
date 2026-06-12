---
title: "Restoring the Main Menu"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by brainrush on 2010-03-09
Hi all, I'm new to these forums and ubuntu, I searched the forums for a solution, but nothing seems to work.

Here's the problem: I deleted the main menu panel by accident.

Here's how it happened: I randomly found I could add things to the panel, I added the little fish and the googly eyes, and after messing with them, I decided to remove the fish. I clicked "delete this panel" it asked for confirmation, and I blindly accepted.
...aaand *poof* it disappeared. Other than the stuff I did 5 minutes before deleting the main menu, it was stock.

The situation:

I can't figure out how to undo it, I've tried typing things into the terminal with limited success, the most successful being:
sudo debconf gnome-panel
taken from the archives in '07.

This restores the main menu, but I'm guessing it logs me onto root because none of my settings are there. a lot of the power options don't work, and when I hard restart, and I'm guessing it logs me on as my user, the menu is missing again.

From what I've used it for, Ubuntu is pretty cool, but I 
Any help would be much appreciated, 

thank you

---

### Post by marshmallow1304 on 2010-03-10
This should do it.  To open a terminal, use Alt+F2 and enter gnome-terminal.

```
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by brainrush on 2010-03-10
Thank you very much, worked like a charm!

Being new and all, would you mind telling me what those commands did? it looked like first the other panel got removed, and then the whole thing restarted.

I'm gonna guess RM means remove?
Pkill would mean start? process kill?

there isn't a babelfish for linux, or is there?
Once again Marshmallow 1304, thank you very much.

---

### Post by marshmallow1304 on 2010-03-10
No problem.

The first command unsets all configurations in the /apps/panel part of the Gnome Configuration.  The second command removes the /home/<username>/.gconf/apps/panel directory.  The third command kills the gnome-panel process so that it can regenerate and reload the settings.

---

