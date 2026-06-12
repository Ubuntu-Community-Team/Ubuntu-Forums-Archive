---
title: "Xubuntu keeps restarting opened applications on startup"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by demiliterizedzone on 2009-05-28
Title:  Xubuntu keeps restarting previously opened applications on startup

Anyone know how to disable this feature?  I have the latest version of Xubuntu, 9.x (sorry forgot), and everytime I restart the applications which I had opened when I shut it down keep reappearing.  I did not add these as startup processes.

Kind regards,
-DMZ

---

### Post by kerry_s on 2009-05-28
do you have the save session on exit checked in session&startup?

---

### Post by demiliterizedzone on 2009-05-28
"XFCE Session Manager - The session manager allows the user to save sessions and restore them after login. It is capable of saving several different sessions. It also provides an easy way to log out, reboot, shutdown, hibernate or suspend your computer."

This is definitely the culprit.  Yes I have turned that option off to NOT save the session state when logging off.

Is there a another place where that option can be enabled?  Currently, I've only found one:  Applications-> Settings -> Xfce 4 Settings Manager -> Session and Startup -> checkbox found.

---

### Post by lisati on 2009-05-29
This isn't Windows - you can always close all running programs before shutting down or logging off.

---

### Post by demiliterizedzone on 2009-05-29
> **lisati said:**
> This isn't Windows - you can always close all running programs before shutting down or logging off.

And I have.  XFCE still remembers the state upon login and it is very annoying.  Maybe I need to manually edit its config file as root (sudo), perhaps the change I am making -- to not save the session state -- is not being saved.  Hrm.. back to googling.

---

### Post by kerry_s on 2009-05-29
> **demiliterizedzone said:**
> "XFCE Session Manager - The session manager allows the user to save sessions and restore them after login. It is capable of saving several different sessions. It also provides an easy way to log out, reboot, shutdown, hibernate or suspend your computer."

This is definitely the culprit.  Yes I have turned that option off to NOT save the session state when logging off.

Is there a another place where that option can be enabled?  Currently, I've only found one:  Applications-> Settings -> Xfce 4 Settings Manager -> Session and Startup -> checkbox found.

on the bottom of the logout dialog.

---

### Post by demiliterizedzone on 2009-05-29
> **kerry_s said:**
> on the bottom of the logout dialog.

Thank you kerry_s that was it, though I also discovered it (finally) the other night.  The reason why I never saw that checkbox was because I was shutting down from terminal and it must have been enabled on the logout dialog.  Thank you everyone, appreciate the input.

---

### Post by scottbomb on 2012-04-20
Sorry to resurrect a dead thread but this is happening to me. The checkbox "Save session for future logins" is NOT CHECKED.

It keeps opening Firefox and a pdf reader on startup. I close them and reboot. There they are again!

---

### Post by Toz on 2012-04-21
Try clearing the cache. Delete the ~/.cache/sessions directory. The .cache directory is a hidden directory in your home directory.

---

### Post by scottbomb on 2012-04-26
That does seem to do the trick. Unfortunately, it does it again after a later re-boot.

I may have to add this command into a script to make it happen every time. I'd prefer to have it done on shutdown. Is there a specific place I can put it to run as su on shutdown?

---

### Post by Toz on 2012-04-26
When you log out, there is an checkbox option to save your existing session (bottom of the logout dialog). If it is checked, it will save all open programs and restart them on next log in. If you don't want this behaviour, clear the cache as above and make sure this option isn't checked on logout.

---

### Post by scottbomb on 2012-04-26
The problem I'm having is that it's relaunching applications I had open in the prevs session even though I have that box unchecked. In fact, I can close the applications, shut down the computer, turn the computer back on, and it launches those same applications. Very strange.

---

### Post by Toz on 2012-04-26
I think you're caught in a loop. Try this.

1. Log out with checkbox unchecked
2. Go to the first tty (Ctrl+Alt+F1), login and run:
```
rm -rf ~/.cache/sessions
```
3. Go back to the gui (Ctrl+Alt+F7) and log in again
4. Test it.

---

### Post by scottbomb on 2012-05-01
Thanks, Toz. That seems to have fixed it and it hasn't come back. It puzzles me because I did delete those files earlier but from within the X11 environment, not tty like you mentioned.

And speaking of tty, I'm beginning to like it better than the windowed version of bash for certain tasks.

---

### Post by scottbomb on 2012-05-19
It still has a tendency to do this if I 

a. tick the box to save my session and shut down
b. later boot up and the session restores
c. then close session and UNTICK the box
d. next boot up, session is restored even though it wasn't supposed to be. Per the xfce 4.10 release notes, this may have been fixed. I will attempt to install it today and see how it works.

---

### Post by Toz on 2012-05-19
Yes, thats the default behaviour now. I just saw a bug fix report where this has been fixed. Not sure when it will be ported to 4.10 precise/quantal installs.

Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/704650]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/704650")

---

### Post by Jose Catre-Vandis on 2012-05-22
I read this thread with interest a couple of days ago, and then it happened to me too!  (I have a similar problem on a car forum where I read about someone else's broken something or other, then the one on my car breaks too!!) :)

---

