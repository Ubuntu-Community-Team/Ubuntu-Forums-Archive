---
title: "Problem with adding Xubuntu desktop to Ubuntu"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by davesalyers on 2011-08-19
I am currently using Ubuntu 10.04 (Gnome). I installed the Xubuntu desktop package as I wanted to switch to XFCE. My plan is to upgrade to the newest version of Xubuntu eventually as I am not interested in Unity or GNOME3. This worked okay for a while, but when I try to start an Xubuntu session it pulls up the wallpaper from my GNOME session which is over my XFCE session which does not allow me to see the toolbar, etc. I just have the wallpaper and the mouse cursor. When I use the regular GNOME session everything works just fine.

How can I fix this so I can use both the GNOME and Xubuntu XFCE desktop?

---

### Post by bodhi.zazen on 2011-08-20
In your xfce settings menu go to "Sessionand Startup"

Go to the the advanced tab and make sure the "Launch Gnome services on startup" is not selected.

When you run nautilus, be sure to run it with the --no-desktop option.

Other then that, I am guessing your xfce configuration is kaput. Try running it as another user. It it works as another user, you can try moving your ~/.config/xfce4 directories (to say ~/.config/xfce4.bak and ~/.config/xfce4-session.bak )

---

### Post by rojaasensei on 2011-08-20
Have you tried this?

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by davesalyers on 2011-08-20
I tried the solutions that were suggested but was getting error messages as some of the packages were not found. So I used this as an opportunity to do a clean install of Xubuntu 11.04 on my system this morning which had no problems with the hardware and works very fast and smooth - better performance than I had before with GNOME!

:D

---

