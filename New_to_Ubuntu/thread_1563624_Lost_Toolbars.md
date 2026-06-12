---
title: "Lost Toolbars"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by rocknrollmouse on 2010-08-29
Hi,

I have lost both toolbars (top and bottom of screen), how can I recover therm?
 
Just installing ubuntu 10.04, basic install went ok; first update ok (but slow #3hours - v.slow internet connection); in the process of downloading ubuntu-restricted-extras package (2 hours download gone; about 1.5 hours download to go) when power cut to house.  Re-starting the pc, ubuntu appears to load ok, and allow me to log-in, but only the desktop loads (ie the wallpaper(still default)), no toolbars; right-click on the desktop brings up desktop options, but no terminal, or applications. 

Help! How do I get the toolbars back?:confused:

---

### Post by Naitsirhc Hsem on 2010-08-29
[http://ubuntuforums.org/showthread.php?t=1404506&highlight=reset+gnome+pannels](http://ubuntuforums.org/showthread.php?t=1404506&highlight=reset+gnome+pannels)

use the search on this site

---

### Post by BrockStrongo on 2010-08-29
try typing this into terminal
gconftool &#8211; -recursive-unset /apps/panel

Hope this works for you

---

### Post by conradin on 2010-08-29
I think what you mean is the gnome-panel. Is this right? are you using gnome?
If so, press, ctrl+alt+F3, then type:
(you will have to log in)
```

sudo apt-get install gnome-panel

```
let that install / reinstall, 
then shift back to the graphical mode, ctrl+alt+F7, and check it out.
you might have to log out, and log back in for it to take effect.

---

### Post by rocknrollmouse on 2010-08-30
Hi,

Thanks to all who replied.
Some progress, as I can now get the toolbars back, but they disappear after a re-boot.

To get the toolbars back:

[INDENT]from the desktop, [Alt]+[F2]
choose "gnome-terminal" from dropdown;
in terminal enter the following three commands:

```
gconftool-2 –-shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```[/INDENT]

This procedure brings the toolbars back (I think it recreates the default toolbars), but they disappear again after re-boot.
Can anyone suggest how to make them permanent?

Don't know if this helps or takes us back a step, but on last re-boot I put a file on the desktop, since the re-boot the file isn't shown - however if I go to [COLOR="DarkRed"]Desktop[/COLOR], from the [COLOR="DarkRed"]Places[/COLOR] menu, the file is shown:confused:  (file doesn't show before or after re-loading the toolbars.

  --//--

Other actions taken from the advice given (again thanks to all):
> I think what you mean is the gnome-panel. Is this right? are you using gnome?

Yes, I have gnome (I am using plain ubuntu 10.04, so no prefix).  The bars in question are the one at the top, and one at the bottom of a 'plain' gnome install (this hasn't (yet) been customised).

> If so, press, ctrl+alt+F3, then type:
(you will have to log in)
Code:

sudo apt-get install gnome-panel

let that install / reinstall,
then shift back to the graphical mode, ctrl+alt+F7, and check it out.
you might have to log out, and log back in for it to take effect.
Good idea, but no change.  The apt-get line returns zero changes, as everything is "installed".

> try typing this into terminal
gconftool – -recursive-unset /apps/panel

Hope this works for you 
This was the first I tried, as it seamed short and quick, but sadly didn't work in this case.

---

### Post by rocknrollmouse on 2010-09-17
bounce

---

### Post by rocknrollmouse on 2010-09-21
last call of a desperate man: 

*anyone any ideas please?*

before I give in and re-install :confused:

---

### Post by Naitsirhc Hsem on 2010-09-21
have you tried creating a new user?

---

### Post by rocknrollmouse on 2010-09-21
Hi Naitsirhc,

Just tried adding a new user.  

On first login, toolbars created as expected.  
However, on subsequent logins, no toolbars :(

---

