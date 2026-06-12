---
title: "Why Do My Desktop Icons keep dissapearing???"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by oxf on 2009-06-21
I Installed Jaunty and am very pleased with how its working. I've been setting up various preferences etc etc.etc......and all looking very good.

Then just now I rebooted and all my Desktop icons have gone. Everything else looks fine including the background and things appear to work fine, just the Icons are gone!

I went to drag a few back and as soon as I let go of the mouse the Icon just quickly goes up to the top bar and vanishes again. What did I do wrong here? I assume I set something wrong (at least i hope so!)

Any ideas?

---

### Post by oxf on 2009-06-21
The only thing I should add is I turned off a few startup apps I don't need and I removed via Synaptic Pkg Mgr -all- the Bluetooth applications since I don't have anything Bluetooth here. I wouldn't have thought that would have affected anything?

---

### Post by loell on 2009-06-21
you should still have the terminal in your accessories menu, from there, try to execute **nautilus**, see if there's any error message or if the desktop icons are back.

---

### Post by oxf on 2009-06-21
> **loell said:**
> you should still have the terminal in your accessories menu, from there, try to execute **nautilus**, see if there's any error message or if the desktop icons are back.

When I type "gksu nautilus" Nautilus wont launch at all!!:confused:
What have I done??

---

### Post by ubuntu27 on 2009-06-21
Install or Re-install **ubuntu-desktop** meta-package using the terminal or synaptic package manager
```

sudo apt-get install ubuntu-desktop
```

---

### Post by oxf on 2009-06-21
> **ubuntu27 said:**
> Install or Re-install **ubuntu-desktop** meta-package using the terminal or synaptic package manager
```

sudo apt-get install ubuntu-desktop
```

OK I just did that using terminal. 
What I noticed was that a number of packages containing the word "bluetooth.." were installed. this may have been my mistake because I removed everything under "bluetooth" thinking I wouldnt need them as I dont have bluetooth devices. 

Now when I type "gksu nautilus" I get:
mbdb@L100:~$ gksu nautilus

** (nautilus:5600): WARNING **: Unable to add monitor: Operation not supported

Looks like I shouldnt have messed with bluetooth??

---

### Post by gettinoriginal on 2009-06-21
Hit F2, and then type ```
gconf-editor
```, open apps, nautilus, preferences, and make sure that "show destop" is ticked on right side.
You can also add gconf-editor to your applications menu by right click on Applications, edit menus, system tools and tick gconf-editor.  You may have to reboot for the changes to take effect.  :P

---

### Post by ajgreeny on 2009-06-21
Open synaptic and go to File>History.  Find the date that you removed all the bluetooth apps and make sure that everything that is in that removal list is reinstalled.  I know that when I was going to do the same thing using synaptic, **libbluetooth3** would have removed a lot of things that were essentail for my desktop, including nautilus, so I left that alone.

Here's the list of things that would have gone with that lib package, so double check they are all there, and if not reinstall them.  It may be that not all of these are required for the ubuntu-desktop which you have reinstalled, as I understand it.

nautilus
obex-data-server
evolution-indicator
evolution-exchange
pulseaudio
evolution
totem-plugins
libpisock9
ubuntu-desktop
gnome-pilot-conduits
gnome-pilot
libgnome-pilot2
libbluetooth3
evolution-plugins
nautilus-share
gvfs-backends
totem
libpisync1

Good luck!

---

### Post by 73ckn797 on 2009-06-21
I do not use any bluetooth or accessibility features as of yet. Instead of uninstalling them I go to System/Accessories/Main Menu. From there you can deselect them from showing up on the menu. Later if you do want one of those or any other app to be listed in the menus, simple re-enable them in the same way. The disk space consumed by those features is very little to worry about so I leave that alone.

Right clicking over the menu bar also gives the option to edit menus.

---

### Post by oxf on 2009-06-21
> **ajgreeny said:**
> Open synaptic and go to File>History.  Find the date that you removed all the bluetooth apps and make sure that everything that is in that removal list is reinstalled.  I know that when I was going to do the same thing using synaptic, **libbluetooth3** would have removed a lot of things that were essentail for my desktop, including nautilus, so I left that alone.

Here's the list of things that would have gone with that lib package, so double check they are all there, and if not reinstall them.  It may be that not all of these are required for the ubuntu-desktop which you have reinstalled, as I understand it.

nautilus
obex-data-server
evolution-indicator
evolution-exchange
pulseaudio
evolution
totem-plugins
libpisock9
ubuntu-desktop
gnome-pilot-conduits
gnome-pilot
libgnome-pilot2
libbluetooth3
evolution-plugins
nautilus-share
gvfs-backends
totem
libpisync1

Good luck!

Thanks everyone!
I actually just did a clean install (since I hadn't got to the stage of putting all my personal settings and stuff on) So its all back to normal.:D

I guess I learnt the hard way here. But honestly didn't realise that any of the bluetooth packages would affect other things. Ideally I'd love to find a list of what is safe to remove and what isn't but thats probably hoping for too much

---

### Post by ajgreeny on 2009-06-21
I find that a good reason for using synaptic to remove packages, it flags up a list of other things to be removed as well, and you can immediately cancel that particular package removal, ie in my case **libbluetooth3**, which I left, but all the rest of the bluetooth packages were removed with no problem.  I know apt-get remove tells you when other things are to be removed as well, but it is not nearly as striking or obvious a warning as in synaptic.

---

