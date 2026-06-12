---
title: "Touchpad suddenly stopped responding"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by robfuller on 2010-11-11
Hello,

I am using a Lenovo X100e laptop, running Ubuntu 10.10. I overloaded the processor yesterday and crashed Ubuntu, and since then the touchpad will not respond.

Strangely, the touchpad works and moves the pointer while the Ubuntu login screen is showing, but it stops responding once I log in. My laptop also has a small button in the middle of the keyboard to move the pointer: that still works, even when the touchpad does not.

Does anyone know what the problem is?

Thanks in advance,
Rob

---

### Post by NightwishFan on 2010-11-11
Try logging in the Gnome fail safe session.

---

### Post by robfuller on 2010-11-14
NightwishFan: Do you mean select "Ubuntu Desktop Edition (failsafe mode)" when I log in? Unfortunately that doesn't make any difference.

---

### Post by Asele on 2010-11-15
Ubuntu 10.10
All updates current as of this posting
Acer Aspire 5536-5142

I have the same issue.  Touch-pad works at login screen and if i move it during the login process it works until about halfway through the login sound.  If I log in as root touch-pad works fine.

Everything seems normal looking at System>Preferences>Mouse
Tried renaming Home>.dbus to Home>.dbus.old forcing a new .dbus to be created
Tried the command line suggested in a thread I can't seem to find in my history now that involved a command line that ended with touchpad_enable true (or something close to that)

None of it works.  Didn't have the problem yesterday, but I got an update message yesterday so I installed the updates.  When I installed the updates I had my touchpad disabled using the physical key next to the touchpad and it was still disabled during the shutdown at the end of the night.  I noticed the problem when I booted up today.

EDIT: I'm making this post from failsafe mode with the problem still persisting the same.

---

### Post by robfuller on 2010-11-15
My touchpad has just as suddenly started working again, and I have no idea why. It was in the middle of a session (i.e. not after restarting or logging in or out), and I didn't run a system update. But it seems to be fine now.

Any idea why this happened? Or what to do if it happens again?
Rob

---

### Post by NightwishFan on 2010-11-15
If it happens again check the logs for any information (system -> preferences - log file viewer). Syslog is a good place to look.

---

