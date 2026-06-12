---
title: "All Firefox windows &amp; dialog boxes open vertically maximized"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by watchpocket on 2011-06-28
I'm preparing for a clean install of Natty and want to clean up old customizations for possible re-use of some of them once Natty is up, and so that none of my current setup messes things up in the new.  (Still using Karmic right now.)

One major problem  is that within Firefox (and even, maybe, to some extent outside of FF), all of my windows and dialog boxes, when I open them, are in a vertically maximized state. (I can adjust, of course, but to close and re-open means they're vert-maxed again.)

I'd like to change that, so that they ***aren't ***vertically maximized when I open them.

I use (and have always used) the Metacity windows manager.  

And System --> Prefs --> Appearance --> Visual Effects has always been set to "None."

I think I long ago deliberately set this vertical-maximization, but I don't remember where or how.

Also (outside of FF) there are two places where I have the opposite problem -- I ***want*** the windows to open vertically maximized, and they don't: (1) System --> Prefs --> Keyboard Shortcuts; and (2) Terminal --> Edit --> Keyboard Shortcuts.  

For (1) above, I've tried to get this working with Devilspie using the other name for this Keyboard Shortcuts, which is "gnome-keybinding-properties" (which is also its command under "Launcher Properties" -- I have it in the gnome top panel) but my Devilspie for this isn't working.

Any tips appreciated.

I'd also like to know the name to use in Devilspie for the Terminal's Keyboard Shortcuts.

(P. S.  Please, before advising just to use Devilspie or wmctrl for windows issues, I have both these, but need first to unset this bad default.  Thanks.)

---

### Post by cariboo on 2011-06-29
I would suggest if you plan on doing a clean install of Natty, that you also remove all the configuration files and directories from  /home/$USER, there are enough changes in Natty, that using configuration files from a previous version will cause problems.

---

### Post by watchpocket on 2011-06-29
> **cariboo907 said:**
> I would suggest if you plan on doing a clean install of Natty, that you also remove all the configuration files and directories from  /home/$USER, there are enough changes in Natty, that using configuration files from a previous version will cause problems.


Well, it goes without saying that everything will be wiped.  But I'll definitely be backing up and re-using, for example, my config files for vim and zsh which I use in the terminal, and a few other things.  I wouldn't try to re-use old desktop configs from Karmic in Natty.  But until I do the install -- it may yet be another month or two -- this is one issue I'd still like to resolve.

---

