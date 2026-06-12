---
title: "how to change panel icon"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-27
i am trying to swap out the shut down icon from my theme, but it wont copy over to the appropriate theme. 
1. the button seems to be a .png not sure though and the only icon for shut down is in the 48x48 folder of the theme. 
2. the only .png i found for another theme to do the same thing is not a 48x48 .png it is another size?
3. i tried to do it as root but didn't seem to work, i may have had too many windows open and lost track of which was the root window and which one was the user window. 
any ideas how to swap out an ugly icon in otherwise a great theme. Since it is on the panel it does not give the option to go to properties to change th icon on the fly as for desktop icons or sub-menu icons in menu editor. any ideas?????

---

### Post by drs305 on 2009-05-27
For the default Jaunty setup, the shutdown icon at the top right of the panel is called "system-shutdown.png". For me, the icon is in /usr/share/icons/gnome/24x24/actions. 

I made a backup of the original file /usr/share/icons/gnome/24x24/actions/system-shutdown.png and then modified the file using gimp. When I refreshed the panel (killall gnome-panel) the changes were reflected in the icon.

Your setup may be different, but the file is probably named the same regardless of the size if you are using the default Human theme. You can do a universal search for the icon and then determine which one you are using. Rename it, and name your replacement icon "system-shutdown.png", and refresh the Desktop. That should do it.

To find this icon:
```

sudo find /usr/share -type f -name "system-shutdown.png"

```
Most icons are located in one of the subfolders of the above. If you don't locate the icon, use "/" instead. You will probably find the icon in various sizes. Mine was 24x24 on my laptop.

---

### Post by DarinB on 2009-05-27
i got the desired icon transfered using gksudo nautilus i renamed the orginal icon 1system-shutdown.png and renamed the new icon system-shutdown.png but as soon as i hit enter it locked (a little pad lock on it and an x)the permissions tab said root read and write and the execute button was checked but on re log on the icon was generic so not icon when i went into the usr/share/icon folder under user the icon was gone ie generic when i went under root it was there. when i tried to unlock it by changing the permissions via the permissions tab it wouldn't let me. any ideas i got the new icon there as gksudo nautilus but then got stuck????????

---

