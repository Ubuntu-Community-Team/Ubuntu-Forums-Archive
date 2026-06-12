---
title: "No keyboard or mouse at login"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Midgetprawn on 2009-10-21
Not an original query but I have tried other suggestions and failed to make progress. Running 9.04 for several months without problems. I was resetting chown 644 as I had an error statement and now I can't use my keyboard or mouse at login. Tried cntrl-alt-f2 to get console - no joy. I can't cntrl-alt-backspace or del.
Booted in recovery mode where keyboard works OK
Running off a live session just now.
Any suggestions/

---

### Post by dvlchd3 on 2009-10-21
What do you mean by "resetting chown 644"?

---

### Post by Midgetprawn on 2009-10-21
I had a permissions error due some conflict with ./dmrc

---

### Post by Midgetprawn on 2009-10-21
I am currently booted in recovery mode. The Keyboard functions OK until I run gdm and get to the login page. I have tried apt-get update to improve packages, I have repaired broken packages and run fschk. Xorg log does not show errors.
Any suggestions from here. I could backup and reinstall

---

### Post by Midgetprawn on 2009-10-21
Still here ploughing through sites and tricks.
I have succeeded in fixing a hal error which came up running fsck and  finding shared blocks and a startx error and finally logged into and xfce desktop only to find my mouse and keyboard are still not responding.

A reinstall?

---

### Post by Mike_IronFist on 2009-10-21
> **Midgetprawn said:**
> Still here ploughing through sites and tricks.
I have succeeded in fixing a hal error which came up running fsck and  finding shared blocks and a startx error and finally logged into and xfce desktop only to find my mouse and keyboard are still not responding.

A reinstall?

Yes, but I suggest you download and burn a new disc - if you reinstall with a disc that had issues after install, it may (or may not) cause problems again.

---

