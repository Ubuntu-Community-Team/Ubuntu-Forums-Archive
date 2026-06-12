---
title: "Panels - Adding things to them and rebuilding them"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by zcacogp on 2010-02-06
Chaps, 

This is probably quite a simple one. 

I'm running Ubuntu (9.10 Karmic), and have a number of things on the top and bottom panels. 

I've just installed Cairo-Dock, and am quite liking it. In fact, I am **very much** liking it ... I am thinking of getting rid of the top and bottom panels on the screen, and going over to just using Cairo-Dock. (Does anyone have any general comments on this BTW? Good idea or a really, really bad one?) 

If I was to get rid if the top and bottom panels, and later decide that I want to get them back, is there a command that rebuilds them? As in, rebuilds them to the standard installation (with "Applications", "Places" and "System" at the top, and the workspace switcher at the bottom)? 

Also, I have a few extra bits on the top panel - Ubuntu Eyes, Lock and System Monitor. Is it possible to put these in Cairo-Dock, or on the desktop? (If they go on the desktop, would this be via desklets/screenlets, or is there another way?) 

Thanks for any help ... 


Oli.

---

### Post by theozzlives on 2010-02-06
I tried Cairo dock and didn't find a shut down menu I liked, so went back to GNOME-Panel. Tried AWN also.

---

### Post by Temposs on 2010-02-06
You would have to rebuild your GNOME panel from scratch if you get rid of it, but it's easy to do. Just right click on the desktop and one choice is "Add Panel". Once you have your new panel, right click on it and do "Add to Panel", and then you can put whatever you like on it. So, you can rebuild your panels in a minute or two, depending on what you had on them.

If you don't like Cairo Dock or AWN, as theozzlives seems not to, another alternative is to get GNOME-Do and enable the Docky theme. This is my favorite dock solution and I've been using it for quite a while now.

---

### Post by drs305 on 2010-02-06
You can save and restore your panels with the following two commands, as long as you don't try to put them on a different computer or delete the associated files:

To Save:
```
gconftool-2 --dump /apps/panel > /path/filename
```

To Restore:
```
gconftool-2 --load /path/filename
```

---

### Post by fabounet on 2010-02-07
> I tried Cairo dock and didn't find a shut down menu I liked
yet there is a *logout* applet that can display both logout and shotdown windows (with right-click and middld-click)

---

### Post by zcacogp on 2010-02-07
drs305 - that looks like exactly what I want. Thanks. 

fabounet, thanks for your help with this, and my other thread (about installing things from gnome-look.) Where do you find applets for cairo-dock? And how do you install them? 


Oli.

---

### Post by fabounet on 2010-02-08
by using the [PPA]("https://launchpad.net/~cairo-dock-team/+archive/ppa")

---

### Post by zcacogp on 2010-02-08
OK, I think I am getting there now. Thanks very much fabounet for your help (I assume that you are the same fabounet who has written themes and icons for Cairo-Dock? If so, I am impressed, and thank you again!) 

One last question. OK, two. 

1. In 'Shortcuts', I'd like to add some more shortcuts. (Both to drives which I have on auto-mount under ~/mnt.) How do I arrange for this to happen? 

2. On the gnome top panel there is a "system" menu, with "Preferences" and "Administration" giving access to a number of useful system bits. How can I get this "System" menu onto Cairo-Dock? (I have tried dragging and dropping, which worked a treat with Amarok and Open Office, but it didn't work.) 

If these two can be answered then I'll consider binning both the top and bottom panels and going very minimalist! 

Thanks again for your help. 


Oli.

---

### Post by fabounet on 2010-02-09
about the Menu, the GMenu applet gathers both Applications and Preferences (and also Recent files).

Shortcuts is supposed to display automatically the drives that are listed in Nautilus (and also the bookmarks).
Are thoses 2 drives listed in Nautilus and not in the applet ?
If so, then as a workaround you could consider making a bookmark to these 2 drives, and activate the listing of bookmarks in the applet (if it's not already the case), then you would have them in the sub-dock too.

To answer a previous question, you can also put the Cairo-Dock's applets on the desktop (drag them from the dock and drop them on anywhere you want).

---

### Post by mcduck on 2010-02-09
The Places-menu only lists drives that are mounted inside /media, all other drives and locations must be bookmarked manually. Which is very easy, just browse to a directory you want to add to the Places-menu, and then select Bookmarks->Add Bookmark from the menu (Or Places->Add Bookmark if you are using the spatial mode instead of browser mode).

The System-menu isn't a menu item, so you can't drag&drop it anywhere. But most likely Cairo-Dock already ahs some applet that provides access to System Menu, as well as the APplications & Places-menus, through a single button (think about classic Windows start menu..). AWN sure does but I haven't used Cairo-Dock..

What comes to restoring the Gnome-panel, that's actually simpler than anybody has suggested. Just don't delete your panels, but instead stop the Gnome-panel from starting with your desktop. That way you won't get any panels, but your panel configurations will stay as they are and any time you want to use the panels you can simply run "gnome-panel" to start them.

The panels can be stopped from auto-starting through gconf-editor, just remove the "panel" from the *desktop/gnome/session/required_components_list* -key (or change *desktop/gnome/session/requird_components/panel* to cairo-dock, and Gnome will autoload Cairo-dock instead of Gnome-Panel). Actually that's pretty much the only way to do this, because you can't just t´right-cllick and select "remove panel" to get rid of your last panel. Gnome-panel doesn't allow you to do that. ;)

---

### Post by fabounet on 2010-02-09
actually although adding "cairo-dock" to the gconf key is neecssary, it won't load the dock on startup.
you still have to add the dock on startup (right-click -> cairo-dock -> launch on startup, or do it maunally)

---

### Post by mcduck on 2010-02-09
> **fabounet said:**
> actually although adding "cairo-dock" to the gconf key is neecssary, it won't load the dock on startup.
you still have to add the dock on startup (right-click -> cairo-dock -> launch on startup, or do it maunally)

It doesn't? And you have added it into the panel -key, not the required_components_list -key?

In that case there's no reason to add cairo-dock anywhere, just remove the "panel" from the required_components_list to disable gnome-panel from automatically starting. After that you'll be able to start and stop gnome-panel as you wish.

---

### Post by fabounet on 2010-02-09
nope, it sounds weird but you have to add "cairo-dock" instead of "panel"
if you just let the key blank the gnome-panel will be started.
This is probably a bug in Gnome, since for some people letting blank will be enough.

---

### Post by mcduck on 2010-02-09
> **fabounet said:**
> nope, it sounds weird but you have to add "cairo-dock" instead of "panel"
if you just let the key blank the gnome-panel will be started.
This is probably a bug in Gnome, since for some people letting blank will be enough.
Of course it *could* be a bug, but I can't find a report for such a bug, and I've never seen that happening. To me it sounds more like you (and those people having problems doing this) are just confusing two separate gconf keys.

**desktop/gnome/session/required_components_list** is a key with a list of three components /by default). Remove "panel" from this list and no panel will be loaded. (you can't change this to cairo-dock since this is not where the commands are defined.)

**desktop/gnome/session/required_components/panel** defines what application should be used for the panel component from the above key. *This* is the key you want to change to cairo-dock.

So the first key is a list of components to use, and under desktop/gnome/session/required_components/ you'll find a key for each of those components, defining what program to use for that component.

You have two options, either remove "panel" from the first key (to disable panel) or leave it there, and define whatever app you want to use in the second key to load that app automatically.

---

### Post by fabounet on 2010-02-09
I'm not confusing, I have 2 pc and one is working with letting blank, the other not  (both under Karmic) ;-)

you can find many post here about this problem, even if noone has taken the time to report it on Launchpad.

---

