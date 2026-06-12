---
title: "How do I get a vnc client to start on Xubuntu startup"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-05-16
All I want is to be able to press the power button on my computer, and when Xubuntu starts, I need a vnc client to bet running without me clicking on Application--->Networking--->X11VNC Server---->Apply X11VNC Server. I want it to start on start up like how remote desktop starts in ubuntu

---

### Post by krunge on 2010-05-16
> All I want is to be able to press the power button on my computer, and when Xubuntu starts, I need a vnc client to bet running without me clicking on Application--->Networking--->X11VNC Server---->Apply X11VNC Server. I want it to start on start up like how remote desktop starts in ubuntu
You mean you want a vnc **server** to be running at startup, right?  A vnc client is the Viewer.

It seems like you have your system automatically log in to a desktop session as a user at boot time, correct?  Somehow you need to configure x11vnc to run at XFCE startup for that user. Perhaps Settings -> Session and Startup -> Application Autostart?  If you need help on what the x11vnc cmdline should look like (e.g. use a password) just ask.

---

### Post by theweasel2345 on 2010-05-16
Thanks A Lot!
What does the command line look like

---

### Post by theweasel2345 on 2010-05-16
Never mind, I just went to auto start programs and added vino-preferences. It starts automatically and works great, THANKS!

---

### Post by krunge on 2010-05-16
> **theweasel2345 said:**
> never mind, i just went to auto start programs and added vino-preferences. It starts automatically and works great, thanks!
Bah!  :-)

---

