---
title: "Auto hide"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Habdab on 2009-11-20
Does anyone have any idea if I can auto hide the top bar/panel on the Ubuntu Netbook remix 9.10 launcher page? If so how?

I'd love to have it hidden, as when I open a browser there are so many horizontal bars on the screen it becomes confusing. One less would be a great help. (I don't want to have to keep pressing F11 every time I use firefox)

---

### Post by Kevbert on 2009-11-20
If remix is the same as standard desktop Ubuntu, just right click on any empty taskbar space and select 'Properties'.  Under the 'General' tab you should see an 'Autohide' tickbox.

---

### Post by Pipps on 2009-11-21
I can advise that Ubuntu 9.10 Netbook Remix does not have the normal 'Auto-hide' properties option, when right-clicking on the menu bar.

How else can this bar at the top of the screen be hidden temporarily from view?

---

### Post by Pipps on 2009-11-21
Ah! There appears to be a graphical bug getting in the way of things. Allow me to explain...

On first clicking on the menu bar at the top of the screen, only a useless 'Preferences' option box is available. However, on selecting 'Remove From Panel', on this, and thereby loosing the ability to see which applications are simultaneously open, it is then possible, upon right-clicking on the menu bar again, to access the 'Panel Properties', and thereby activated the auto-hide option.

Hope this helps!

---

### Post by Kevbert on 2009-11-21
> **Pipps said:**
> Ah! There appears to be a graphical bug getting in the way of things. Allow me to explain...

On first clicking on the menu bar at the top of the screen, only a useless 'Preferences' option box is available. However, on selecting 'Remove From Panel', on this, and thereby loosing the ability to see which applications are simultaneously open, it is then possible, upon right-clicking on the menu bar again, to access the 'Panel Properties', and thereby activated the auto-hide option.

Hope this helps!

That should be reported on [[COLOR="Red"]launchpad[/COLOR]]("https://launchpad.net/") then.

---

### Post by Habdab on 2009-11-21
Thank you all for your replies. I managed to sort it out in the end and got it to autohide without removing from panel. I also managed to speed up the appear and hide and to resize the bar so I can see it on my Acer Aspire one without a magnifying glass :)

---

### Post by Pipps on 2009-11-21
> **Habdab said:**
> Thank you all for your replies. I managed to sort it out in the end and got it to autohide without removing from panel.
How on earth did you manage this? :)

---

### Post by jack.harris on 2009-12-03
Have the same with xfce.

How I resolve temporarily it:

if you can't have clean work session if the hide panel bug:
-exit the session 
-open a command (Ctrl + alt + 1)
-del the file:
rm .cache/session/xfce4-session-user-laptop:0

go to gmd panel (Alt + right arrow) x times or  (Ctrl + alt + 7)
start xfce

Then leave xfce session, if the hide panel works well
check the register the session check box and restart it.

when you leave the session, **uncheck** the register session box

all work fine and sometimes hide panel bug again, simply restart the session.

---

### Post by andw on 2010-02-18
It seems it can be done without turning things off / on etc.
The trick is to find a spot on the task bar that is not 'occupied' with something, so that when you right click on it it shows the task menu options, not the options of the item you are clicking on.
I found a spot just to the top right of the speaker icon, just before you hit the date area.
Although it does seem tricky to hit it exactly, and took a few right mouse clicks before the "properties" option was listed.
But once I could click on it, the Auto Hide option was there and worked fine.

---

### Post by JohnnyC35 on 2010-05-17
I'm having the auto-hide issue also. My bottom taskbar doesn't hide unless I goto properties and uncheck and then recheck autohide, or if I kill gnome-taskbar it will then reload the taskbar and then autohide. Very odd bug.

---

### Post by sir_firebrand on 2010-05-18
In the console:

sudo gconf-editor

apps>panel>toplevels>top_level

change:

auto_hide [ ]

to

auto_hide [V]

Know bug:

Some times the bar "stuck" behind some windows.

---

### Post by StaRetji on 2010-06-12
@sir_firebrand

Ubuntu Netbook Lucid Lynx stable = your tip doesn't work.
auto_hide selected, nothing happens, panel is still there.

---

### Post by Pipps on 2010-10-04
This seems to provide the answer:

[http://ubuntuforums.org/showpost.php?p=9924073&postcount=14](http://ubuntuforums.org/showpost.php?p=9924073&postcount=14)

The panel auto-hide can be implemented once the steps in that article are followed.

---

