---
title: "bad menu entries after deleting ioquake"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by rumca.js on 2009-09-03
Helo. I've got problem. I downloaded ioquake3, I couldn't make it run so I downloaded openarena from synaptics package manager. I deleted ioquake3 files, but in menu I still got bad entries for ioquake3 and teamarena.

1. how to remove bad entries
2. how should i remove stuff which I install by   "sh file.run"
3. i updated ubuntu. I think I might have a new kernel now, because grub has additional entries. How to erase old kernel?

---

### Post by Keith Hedger on 2009-09-03
Right click on the Application menu and select edit menus and from there you can add/delete/hide/show menu items

---

### Post by ks07 on 2009-09-03
> **rumca.js said:**
> Helo. I've got problem. I downloaded ioquake3, I couldn't make it run so I downloaded openarena from synaptics package manager. I deleted ioquake3 files, but in menu I still got bad entries for ioquake3 and teamarena.

1. how to remove bad entries
2. how should i remove stuff which I install by   "sh file.run"
3. i updated ubuntu. I think I might have a new kernel now, because grub has additional entries. How to erase old kernel?

[LIST=1]
[*]Follow Keith Hedger's instructions above.
[*]There is no easy way to uninstall things installed like that unless someone has made an uninstall script especially for it. The only way to remove it is to find where it is installed and manually delete it.
[*]Open Synaptic (System > Admin). Quick search for "linux-image" and right click on the kernel number you want to remove. Then choose mark for removal (or complete removal, your choice).
[/LIST]

---

### Post by rumca.js on 2009-09-03
1.

Right clicking on any entry of main manu (for intance "games" is not invoking any popup menu). Right clicking on menu entry inside "games" gives a popup only with options 

Add this launcher to panel
Add this launcher to desktop
entire menu -> Add this launcher to pan ....
                      ->Add this launcher to deskt....

so there was no possibility to edit/add/ anything..... ?

I managed to modify meny by
System->Preferences->Main menu    

2.
I found "uninstall" file in the folder. However it gave me an error of some kind.  That some files were missing, or something similar.
sudo sh ./uninstall
so I deleted everything with delete key, and I modified menu by myself.

3.  thanks :)

---

