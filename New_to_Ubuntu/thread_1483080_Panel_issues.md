---
title: "Panel issues"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by fourstringin on 2010-05-14
I have an issue with the panel and my laptop. I dock the laptop and undock all day. When i do this it rearranges my panel items. or spreads them out.

OR a bigger issue is that some will be geeked out and show half what its supposed to. ie... 1/2 the wifi icon.

Id like to know if that can be fixed, but i found a way to solve it.

run 

sudo killall gnome-panel

if anything id like to make a double clickable shell script to just do the above.

currently i can only get the script to open in gedit.


any direction on making this script double clickable would be great.

---

### Post by ankspo71 on 2010-05-14
Hi,
here is a simple script that should effectively kill gnome-panel.
```
#!/bin/sh
killall gnome-panel
```
save that into a plain file on your desktop with a name such as "killpanel". Next you have to make it executable. Simply right click on it mark it as executable in the permissions tab.
I'm not able to test it with a gnome desktop at the moment, but should work by clicking on it from this point on. If not I'll be back to help more in about an hour.

---

### Post by almufadado on 2010-05-14
In the file properties (right click over the file) -> permissions -> you must make it executable.

---

### Post by formaldehyde_spoon on 2010-05-14
Or add a launcher for ''xkill'' to your menu, and use it to click on any panel to kill them all.

---

