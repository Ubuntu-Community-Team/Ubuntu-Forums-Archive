---
title: "really dumb mistake with icons"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by metallicamike on 2009-02-25
ok so i was trying to free up space on my crappy 5 gig HDD and so i went ahead and deleted all of the default icon themes that i thought i would never use in nautilus except human and GNOME. but now various icons are shown as not found due to my mistake and i must be OCD because its really bothering me :lolflag: and also the boxes for installation removal etc. don't show up in synaptic do I was wondering if there was a link to download them or recover them or get a package in synaptic? P.S. For anyone who cares I fixed my video problem! (see some of my previous threads)):P

---

### Post by metallicamike on 2009-02-25
bump?

---

### Post by kerry_s on 2009-02-25
you could have just uninstalled them. ;)

you most likely deleted hicolor.

just use synaptic to reinstall it.

---

### Post by metallicamike on 2009-02-25
i did. i just reinstalled it and that didnt help :???:

---

### Post by kerry_s on 2009-02-26
did you do a search in synaptic and reinstall all the icons it says you have installed.

---

### Post by Sirron on 2009-02-26
Perhaps you need to re-apply your current theme now that the icons are available? Open up Appearance and select a different one, then reselect your preferred one.

---

### Post by tarps87 on 2009-02-26
If you deleted the icons you should be able to copy them off the livecd

---

### Post by metallicamike on 2009-02-26
in synaptic it says i only have tangerine human gnom and hicolor installed, and to tarps i dont know how to do that. P.S. nice avatar

---

### Post by Tristam Green on 2009-02-26
Install a new icon theme and apply the theme?

Otherwise, backup your home directory and get more experience with rebuilds :D

---

### Post by metallicamike on 2009-02-26
also ever since this incident i get "The NetworkManager applet could not find some required resources.  It cannot continue." every now and then

---

### Post by nortexoid on 2009-08-18
I idiotically did the same thing, though I was very hesitant to delete the default icons and themes. I should've went with my gut.

Anyway, I get the network manager error as well. It runs fine as long as you don't click "ok", except the icons don't display properly.

I reinstalled hicolor but still get the error. I even ran:

```
sudo gtk-update-icon-cache -f usr/share/icons/hicolor/
```

which didn't do anything, even upon reboot.

Deleting an icon theme should NOT take down networking! Anyone have a solution?

---

### Post by nortexoid on 2009-08-18
I notice that there are no files (i.e. icons!) in any of the subfolders in /usr/share/icons/hicolor, even after having reinstalled from synaptic (and manually using the .deb). Does anyone know where the icons can be downloaded in an archive package so that I can just drop it into /usr/share/icons? (As a last resort, could someone zip theirs and send it to me at [email]niburu1@hotmail.com[/email]?)

(I notice that trying to remove the hicolor-icon-theme would require removing a ton of other packages that depend on it, from nautilus to rhythmbox!)

---

