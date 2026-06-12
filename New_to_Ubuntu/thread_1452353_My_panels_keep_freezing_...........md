---
title: "My panels keep freezing .........."
date: 2010-04-11
forum: New to Ubuntu
---

### Post by tahitiwibble on 2010-04-11
Hi guys,

It's the eternal newbie again :(

I have a pretty good video card and had compiz installed with "extra" visual effects and my panels, when I get to about 4 or 5 icons on the side bar, keep freezing at which point I have to re-boot.

Any suggestions? Thanks a LOT in advance.

---

### Post by 2hot6ft2 on 2010-04-12
Frozen & Blank Panels

> **lidex said:**
> Terminal:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by J V on 2010-04-12
Or make a shortcut to xkill (My personal favorite) and click the panel...

---

### Post by sydbat on 2010-04-12
> **tahitiwibble said:**
> Hi guys,

It's the eternal newbie again :(

I have a pretty good video card and had compiz installed with "extra" visual effects and my panels, when I get to about 4 or 5 icons on the side bar, keep freezing at which point I have to re-boot.

Any suggestions? Thanks a LOT in advance.Have you tried disabling Compiz and test if the problem persists?

---

### Post by J V on 2010-04-12
Do you keep doing the icons in the same order? Perhaps one of them (Or a combination) is causing the crash...

Do a ps aux, note the gnome-panels pid, start up another one in a terminal, kill the first one, add the icons and see what happens when it crashes...

---

### Post by tahitiwibble on 2010-04-13
Oh dear ..........

@ 2hot6ft2 - what does that code do exactly? I see "rm" and hesitate.

@ jv - xkill??

@ sydbat - yes I have disabled compiz and gone back to no enhanced visual effects at all and it still happens.

@ JV - I'm sorry but I have no idea what "Do a ps aux, note the gnome-panels pid" means at all.

I should have been more explicit. What I have on my desktop is a top panel with all my favourite short-cut icons to my most used programs, this is the default panel which apppears when you install Ubuntu. I also have one extra panel to the right of the screen with Trash, Show Desktop and 1 Window List module on it. Everything freezes when the Window List gets to about 5 or 6 links in it.

I'm very grateful to you all.

---

### Post by J V on 2010-04-13
That code removes the files under "~/.gconf/apps/panel" which contain the settings for gnome-panel

xkill is a command that turns your mouse into an X and kills any window you click on, I have a shortcut to <ctrl><alt>X and it works a beauty.

the "ps aux" command shows all proccesses currently running, look down the list for gnome-panel and look at the pid field, this will tell you the id to kill later in my advice...

Your elaboration is interesting...

Do you mean *everything* freezes, or only the panels? Try the xkill I mentioned.

---

### Post by tahitiwibble on 2010-04-13
> **J V said:**
> That code removes the files under "~/.gconf/apps/panel" which contain the settings for gnome-panel

xkill is a command that turns your mouse into an X and kills any window you click on, I have a shortcut to <ctrl><alt>X and it works a beauty.

the "ps aux" command shows all proccesses currently running, look down the list for gnome-panel and look at the pid field, this will tell you the id to kill later in my advice...

Your elaboration is interesting...

Do you mean *everything* freezes, or only the panels? Try the xkill I mentioned.

When the freeze sets in I can close all open windows but the two panels I described become useless (as in frozen and unresponsive) and the only icon that will respond and call back a window is Skype for some reason.

Many thanks to you for your time and the explanations. I think I need a keyboard short-cut to the terminal

---

### Post by tahitiwibble on 2010-04-13
Oh wow, I just experimented with xkill. Can this command be dangerous? I can see it helping with my problem as when I "killed" the panel it came right back again.

---

### Post by tahitiwibble on 2010-04-20
I have followed the instructions to the letter in this howto [https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts) ("Text Entry Shortcuts" sub heading)

When I try to record a shortcut that activates xkill and launch "xbindkey-config" in terminal I get this message

```
Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libatk-bridge.so": libatk-bridge.so: cannot open shared object file: No such file or directory
```

Can anyone help?

---

### Post by tahitiwibble on 2010-04-21
This keeps happening to me; I'm not sure how or why, but the xkill keyboard shortcut problem is solved despite getting the same error message as mentioned above. I shall report back as to whether the xkill shortcut solves my freezing panels dilemma the next time they freeze. :)

---

### Post by tahitiwibble on 2010-04-21
Problem solved (sort of anyway). Using the xkill keyboard shortcut the panel goes away and comes back unfrozen. :P

---

