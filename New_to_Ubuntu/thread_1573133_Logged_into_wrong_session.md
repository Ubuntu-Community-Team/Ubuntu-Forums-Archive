---
title: "Logged into wrong session"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by mikee55 on 2010-09-12
Hi, this has been covered before, but I'm afraid to search. I have a temporary system running on an SSD, which I'm not sure if its aligned, however, my problem is, I logged out of my Gnome Session on my main machine. Then, I logged into the wrong session, when Ubuntu boots, I just get what looks like a Terminal. How do I get Gnome back, please?

Mike:(

---

### Post by col48 on 2010-09-12
Maybe this will help - or provoke something more helpful from someone else.  This is copied from the Ubuntu help for Gnome:
####################################################
    * GNOME 2.14 Desktop System Administration Guide
    * Session Management

A session occurs between the time that a user logs in to
the GNOME Desktop and the time that the user logs out. The session manager starts after the Login Manager authenticates the user. The session manager enables the user to manage the session. For example, a user can save the state of a session and return to that session the next time that the user logs in. 

At a minimum, the following applications run in a session:

    * The session manager, gnome-session.
    * The GConf X settings daemon, gnome-settings-daemon.
    * The gnome-panel application, which runs the panels in the GNOME Desktop.
    * The Metacity window manager.
##########################################################
So maybe running gnome-session from the terminal will kick things off.

---

