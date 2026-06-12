---
title: "Lost Unity Launcher autohide!"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by Fraoch on 2011-05-05
Suddenly the Unity launcher won't autohide!  It's in the way and blocking the left side of all open windows.

I used this to make sure it was set to autohide:

[http://maketecheasier.com/autohide-unity-launcher-in-ubuntu-natty/2011/04/20](http://maketecheasier.com/autohide-unity-launcher-in-ubuntu-natty/2011/04/20)

...it is, it hasn't changed, but it's blocking my view now and will no longer get out of the way.

I've tried:

```
unity --reset
```

which did reset the Launcher but didn't restore the autohide feature.

Any ideas?

---

### Post by Fraoch on 2011-05-05
Solved with a reboot.

Seems to have been some general failure in Unity.  Some menus would not populate either, and I lost access to a running instance of Text Editor (showed in Launcher but couldn't be accessed).

This seems to have started with an unusual combination of mouse actions - I was trying to move a block of highlighted columns down in LibreOffice Calc - it wasn't working, but somehow the hold-left-click-and-drag was applied to the Launcher which then locked up.

---

### Post by Joe_Dude on 2011-05-21
I had a similar problem just a few minutes ago. The launcher seemed to be hiding normally but when I tried to click anything on the far-left of the screen it was like something was blocking it. Eventually I tried to launch something and it wouldn't launch. Also I couldn't scroll up or down on the launcher. Everything else was working normally though. I just restarted and everything was back to normal.

---

### Post by Buggrit on 2011-07-11
Looks like this is a generic problem as I've seen it twice now. The only solutions I have found so far are
1.) Log off and on again (bit of a pain when you are in the middle of something.)
2.) Open The Compiz configuration manager; choose Unity (under desktop) and change the Hide option to "Never".  This way you will still have the unity launcher there but the windows will make allowances for it.

---

