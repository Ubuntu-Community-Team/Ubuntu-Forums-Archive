---
title: "My USB devices (iPod, camera, cellphone, etc.) don't load/appear"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by hanzj on 2009-08-09
Hello,

I don't know what's going on. When I connect a gadget to my ubuntu computer, I don't see an icon on my desktop. Nor do I see a pop-up window asking me what I want to do. (In Nautilus/Edit/Preferences/Media_Tab, "Ask what to do" is on all the media: CD Audio; DVD Video; Music Player; Photos; Other Media). 

I have used other previous versions of Ubuntu, but this current version, 9.04 seems to be the version where I'm encountering this problem. 


When I plug in one of my gizmos, I expect that I see an icon on my desktop. I also expect that I get a "What would you like to do with the plugged-in USB device?" pop-up window.


When I do sudo lsusb I do see the devices. So I think we can rule out hardware.

Please help.

---

### Post by Tamlynmac on 2009-08-09
Just a quick thought.

**Check** you Gnome configuration editor and assure your auto mounting media.

system tools/configuration editor/apps/nautilus/preferences/media_automount

system tools/configuration editor/apps/nautilus/preference/media_automount_open

Both should be checked.


**If **you want it to show on your desktop check and assure your desktop volumes are visible.

system tools/configuration editor/apps/nautilus/desktop/volumes_visible

Should be checked.

Good Luck and Hope This Helps

---

### Post by hanzj on 2009-08-09
tamlynmac,
I ran gconf-editor and went to apps/nautilus/preferences.
Both
 /media_automount
and
/media_automount_open
have check marks.


/apps/nautilus/desktop/volumes_visible has a check mark too.

So I guess your comment is not the solution, since they already have check marks to begin with.

---

### Post by Tamlynmac on 2009-08-09
Sorry, like I said it was just a quick thought. Perhaps someone else will jump in that's experienced this problem.

Good Luck.

Bump

---

### Post by hanzj on 2009-08-10
bump.

---

