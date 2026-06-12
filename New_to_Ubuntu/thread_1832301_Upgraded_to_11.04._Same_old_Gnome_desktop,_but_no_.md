---
title: "Upgraded to 11.04. Same old Gnome desktop, but no panel"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by canam101 on 2011-08-24
I guess my pc has a graphics card that won't work with unity. I upgraded to 11.04, but when the pc rebooted, it came up with the familiar gnome desktop.

That is fine with me - I can live without the unity desktop.

The problem is that the gnome panel is gone.

Is there any command I can issue to bring it back, or, if not that, to get into some kind of system menu so that I can click on this or that icon to do things? At the moment, if I run 11.04, all I have are the desktop launchers that existed prior to upgrading.

---

### Post by Ghost|BTFH on 2011-08-24
Log in using "Gnome classic" option.  To do so, select to Log Out as current user, when the GDM screen comes up with your user options, select your user name, but then at the bottom, change the login from "Unity" or "Gnome 3D" or whatever it is, to "Gnome Classic", this should fix the issue for you.

Then go get a good video card. :)

---

### Post by canam101 on 2011-08-24
Thanks. I re-booted and also logged out and back in, but I do not see any options on the login screen except to enter my name and password.

The upgrade seemed to go well, so I may be overlooking something.

I finally figured out that the command: gnome-panel
will bring up the panel, so I created a desktop launcher to do it; while it is klunky, it seems to work.

---

### Post by grahammechanical on 2011-08-24
Did you try clicking on your user name and then looking at the bottom panel? Menu options appear after you click on the user name.

Also you can install Unity 2D from the Software Centre. That will be the fall back option on systems lacking the ability to run Unity 3D when we get 11.10. After installation and when you reboot and click on your user name Unity 2D will be an option in the menu.

Regards.

---

