---
title: "How to log in with VNC?"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by Mortuis on 2007-09-03
I click System->Preferences->Remote Desktop
Check Allow other users to view your desktop, Allow other users to control your desktop, uncheck Ask you for confirmation, and check Require the user to enter this password, and set a password.

This enables me to connect to the desktop of my Ubuntu 7.04 computer from my windows computer with VNC Viewer 4.  Unfortunately, on occasion there is a need to restart the Ubuntu computer and I cannot connect to it again without manually logging in at the Ubuntu computer first.  Is there a way to log into my Ubuntu computer remotely from my windows computer?

---

### Post by loaderboy on 2007-09-03
If you find an answer to this it would make my day!
I am setting up a digital picture frame made from an old laptop
and need to log in w/o a keyboard or mouse.
VNC works fine for me as long as I log in to the picture frame first but if the power goes out I will be stuck!

---

### Post by Mortuis on 2007-09-20
Figured it out!
I followed the directions at [this thread]("http://ubuntuforums.org/showthread.php?t=265983") to set up x11vnc and server4vnc.  Then I restart X, which brings up the login screen.  I ssh into the computer, enter > ps wwaux|grep auth to find the MIT-COOKIE auth file (my computer returns   > root      4678  0.3  0.9  17240 10084 tty7     Ss+  14:52   0:02 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
), than start x11vnc with > sudo x11vnc  -auth /var/lib/gdm/:0.Xauth and am able to connect with VNC Viewer 4 to the login menu.  I log in, it kicks me out, I then restart x11vnc with > x11vnc and connect again with VNC Viewer 4 and I'm in!

Next I'm going to figure out how to connect with an SSH tunnel so I have a secure session.  But I'm very pleased to be able to be able to reboot my linux computer from work and not be locked out. :-)

---

