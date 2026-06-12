---
title: "shortcut to pms?"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by adduds on 2011-02-23
Hi there! I just downloaded the latest BETA version of ps3 media server from:

[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

I can execute pms via cd'ing to its directory and './PMS.sh' or through nautilus dbl click the script and select run...

My question is can I get it in the applications --> Sound & Video and make or make a launcher for it....just don't like having to have a terminal open and running constantly or navigating through nautilus

I d/led and installed the deb package from here:

[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589)

on my desktop and it created the applications menu addition?

thanks
ad

---

### Post by kvarley on 2011-02-23
> **adduds said:**
> on my desktop and it created the applications menu addition?

Hit Alt+F2, in the Run Application window type "gksudo nautilus" and hit Enter.

Navigate to /home/username/Desktop, copy the shortcut which is on your desktop to /usr/share/applications/ then close the file manager window and it should appear in the menu.

If not you'll have to create your own desktop file for it to appear in the menu, if you need help with that just shout. :)

---

### Post by adduds on 2011-02-26
> **kvarley said:**
> Hit Alt+F2, in the Run Application window type "gksudo nautilus" and hit Enter.

Navigate to /home/username/Desktop, copy the shortcut which is on your desktop to /usr/share/applications/ then close the file manager window and it should appear in the menu.

If not you'll have to create your own desktop file for it to appear in the menu, if you need help with that just shout. :)

darn i pasted the PMS.sh into applications but doesn't show up there :(

---

### Post by adduds on 2011-03-14
"If not you'll have to create your own desktop file for it to appear in the menu"

so how do i create a desktop file to appear in the menu?

cheers

---

