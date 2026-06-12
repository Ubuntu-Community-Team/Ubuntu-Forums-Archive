---
title: "[SOLVED] Eject button not detected on Dell Inspiron"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by RavUn on 2008-12-03
My eject button is not working.  It worked a while ago (in 8.04) and has recently stopped.  I recently upgraded from 8.04 to 8.10 but didn't notice when it stopped working (before or after).

I went to the keyboard shortcuts and the eject button is set to eject, but the eject button itself is not detected.  I booted to Vista and it works just fine so it's gotta be something with Ubuntu.

Anyway to figure this out?  I have a Dell Inspiron i1318 if that helps.  I know I could set another shortcut, but I don't like having a worthless key on my keyboard.

---

### Post by Keen101 on 2008-12-03
hmm... don't know what to tell you. file a bug report on launchpad.

you could use the terminal command "eject"

and even try to create a custom keyboard shortcut to replicate the lost functionality. [http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

---

### Post by falcon61102 on 2008-12-03
The drive may be locked for some reason and needs to be unlocked.  Try this:

Open /etc/sysctl.conf with gedit with:
```
gksudo gedit /etc/sysctl.conf
```

Towards the bottom of the file you will see a line that looks like this:
```
dev.cdrom.lock=1
```

Replace the 1 with a 0.  Save and exit.  It should now work.  If not, try restarting and then try it again.

---

### Post by RavUn on 2008-12-03
It works, thanks!  The line wasn't there so I added it and now it's working.

---

### Post by falcon61102 on 2008-12-03
Glad you got it working.

---

### Post by lacoona on 2009-11-30
I have a Studio 1737 with the same problem and after I've added the line 
```

dev.cdrom.lock=1

```
the eject is working, but the whole system freezes (mouse pointer, music) till the CD/DVD gets ejected.
Any ideas how to solve this?
Thanks

---

