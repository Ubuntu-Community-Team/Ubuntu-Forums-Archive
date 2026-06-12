---
title: "System freezes when logging into Yahoo"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by lee292 on 2009-02-12
I'm using version 7.10 with all available updates and use a WiFi connected LAN to access the Internet.  For the past month or two, when I try to log in to Yahoo! to check my mail, I get to the login screen and my mouse cursor slows down, then stops, and the whole thing freezes up.  I tried Ctrl-W to exit, but it won't work. The only way I've found that I can get out of it is to hold the power button down until my computer shuts off (not good, I know).  I posted the problem to the Mozilla forum, but so far, no luck.  Help!

---

### Post by RomeReactor on 2009-02-12
Hi. Do you have Flash installed? Please enter:
```
about:plugins
```
in Firefox's address bar, then scroll down and post the entries you get for "Shockwave Flash". Do you have a firewall active, such as Firestarter?

---

### Post by mikechant on 2009-02-13
I don't know the actual cause of your problem but:

> I tried Ctrl-W to exit, but it won't work. 

If the gui isn't responding (mouse pointer frozen) you can try:
CTRL-ALT-BACKSPACE to kill the gui and restart it
or
CTRL-ALT-F1 to get a command line terminal where you can look at/kill processes or shutdown cleanly.

---

### Post by deepclutch on 2009-02-13
launch firefox/browser from a terminal and observe the errors.I think this may be due to flash.
if you can ,download flashplayer-10 beta for your platform(32 or 64) and copy into /usr/lib/firefox/plugins/ directory and try.
PS:why not upgrade to Hardy or Intrepid(8.10)??

---

### Post by lee292 on 2009-02-15
Thanks to all for the info.  It does sound like I need to install flashplayer.  Haven't upgraded because my WiFi connection here is a bit iffy.  May go up to my local community college where they have a T1 line and download Intrepid's ISO.

---

### Post by lee292 on 2009-03-01
Upgraded to Intrepid and it fixed the problem.  Thanks all!

---

