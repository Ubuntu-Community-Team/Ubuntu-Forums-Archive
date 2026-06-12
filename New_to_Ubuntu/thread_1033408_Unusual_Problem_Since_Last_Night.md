---
title: "Unusual Problem Since Last Night"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-01-07
I dont know what I exactly did. But somehow my computer entered an all black screen asking for username and password while using Ubuntu. I entered my info and it just sat at that screen. The screen was like a full screen terminal but didn't go anything (at least to my knowledge). I think I pressed cntrl, alt, and I dont remember the other key. I had to pull the battery and restart the computer. Upon doing that I entered Ubuntu but this time after filling out the username and password, it took a long time to load. I mean longer than usual, it sits at a blank black screen for awhile and then finally loads the desktop. But upon loading it doesn't load my theme and I notice it says Gnome failed to start/load or something of the sorts. I restarted (using menu) and again it takes a long time to load and eventually loads everything (including the theme). Also on occasions the theme will not load until I go into a menu and then it slowly loads. Any ideas?

---

### Post by namdung on 2009-01-07
Boot to *Recovery Mode* and select *Fix X Server*.

---

### Post by decoherence on 2009-01-07
if the above doesn't fix your problem, you can reset GNOME to 'factory defaults' by opening a terminal (Applications > Accessories > Terminal) and typing

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Just a heads up about rm -rf... misusing it can create problems. Please just copy/paste this code. Log in again and you should have a factory default GNOME desktop, hopefully without the flaky behavior.

---

### Post by RookieUbuntuUser58 on 2009-01-07
Seems like last night I accidentally entered recovery mode somehow. I did both fixes above and it seems to have improved. Loading the desktop still seems a bit sluggish compared to before but I guess I can live with it.

---

### Post by Denestria on 2009-01-07
Ctrl+Alt+F# keys will give you a "full screen terminal".   All you have to do to get back to graphics mode is Ctrl+Alt+F7 (or sometimes it's Ctrl+Alt+F9).

---

### Post by decoherence on 2009-01-07
> **Denestria said:**
> Ctrl+Alt+F# keys will give you a "full screen terminal".   All you have to do to get back to graphics mode is Ctrl+Alt+F7 (or sometimes it's Ctrl+Alt+F9).

To build on this post, one thing you can do is log in to the console and run the top command. Then switch back to graphical mode and log in, then quickly switch back to top on the console and see if there's a process bogging things down.

A rogue process is not the only potential cause, though.

---

### Post by RookieUbuntuUser58 on 2009-01-07
Would you be able to detect a problem if I post up my bootchart, that may be causing these problems?

---

### Post by decoherence on 2009-01-08
Depends on what the problem is.

Try this in the console

> tail -f /var/log/messages > ~/messagesLog.txt &
tail -f /var/log/X11/messages > ~/x11Log.txt

leave these commands running (the first will go in to the background... just type the next one and hit Enter again) and log in. Once you're completely logged in, go back to the console and run

> kill %1
kill %2

Back in the GUI you should find two new files in your home directory (messagesLog.txt and x11Log.txt) -- you can copy and paste their contents here.

From this we should be able to determine whether there are configuration problems that are causing a timeout or something similar.

---

### Post by decoherence on 2009-01-08
double post!

---

