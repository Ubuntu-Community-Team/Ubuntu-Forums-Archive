---
title: "Xfdesktop in Gnome"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by andr3w on 2009-01-24
Ubuntu 8.10 x64

I would like Xfdesktop (from xfce4) to draw the desktop in GNOME in order to have a right click menu.

I've checked out the measly GNOME extensions and find them inefficient in comparison- so.

If anyone knows how to...

---

### Post by gjoellee on 2009-01-24
This is more like running GNOME in Xfce though:
```
sudo apt-get install xfce4 && sudo apt-get install xfce4-goodies
```or if you want to install Xubuntu (nto recommended if it is speed you are looking for:
```
sudo apt-get install xubuntu-desktop
```(You can remove parts of Xfce later if you would like to)

Then log out. In the login screen click on "Sessions" and then find "Xfce4". Then log in as normal, and make Xfce your default desktop. Now you should see the default Xfce desktop (which is quite simple). It is time to customize! 

Now in the menu you should find "Xfce 4 Setting Manager". Now select "Sessions and Startup". Now go to the "Applications Autostart" tab. Add the follwing:

Name: Gnome Panel
Description: Panels
Command: gnome-panel

then click on OK.

Open a terminal and type in: ```
gnome-panel &
```Now click on the "Session" tab and terminate "Xfce4-Panel" then make sure you don't have any other programs running you don't want at startup, and click on "Save Session". Log out, and log back in. You should now have gnome-panel running.

Now go back to "Xfce4 Settings Manager" and start customizing your desktop. Please tell if you wonder about anything!

---

### Post by andr3w on 2009-01-24
Hm.
Yes, and that seems a bit out of the way for me, but if I don't find anything I've already installed xfce4 so I'll switch over and do this.

Interesting way of doing it from the inside out. :)
Thank you.

---

### Post by andr3w on 2009-01-24
Ok. Well for one:
There is no "Applications Autostart" tab.

Nor is there... any indication of an *area* in which I would be adding anything.

There is no "Sessions Tab" in which I would be terminating the "Xfce4-Panel" either. 


Sure, I got the panel working-
But I just plain **don't like** using the xfce4 environment. It's too... **sparse.**
I'm trying to **ADD** functionality to the already functional GNOME desktop environment, not Take Away nautilus and Everything else along with it in order to right click to Ffox or w/e other app..

Thanks for the suggestion-
But I feel this **will not do.**

Even if it did, the GNOME panel has been increased in width by 6 pixels (I don't think so.)

---

### Post by andr3w on 2009-01-24
Bump.

---

