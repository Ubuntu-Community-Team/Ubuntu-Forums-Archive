---
title: "Strange Video problem with 11.04"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Jolicoeur on 2011-05-13
Installed 11.04, works great. Thought I would try out a few different video players. Tried to play a video file on my hard drive a video program and after about 4 seconds the whole monitor goes black, no sound, nothing. Had to manually reboot. Tried a different player same thing. Tried a couple more same thing. Then I tried a dvd in my drive, same thing.  :)Any ideas? Thanks

---

### Post by jtarin on 2011-05-13
Start one of these applications in the terminal and watch for errors.When and if the screen goes black switch over to a'virtual console'. If you hit ctrl+alt+f1 (through f6), you'll get a text based terminal, with ctrl+alt+f7 to bring you back to where you were.

So, what you want to do when the screen goes black is this:
-switch to a virtual console: ctrl+alt+f1 (through f6)
-stop the display manager: sudo /etc/init.d/gdm stop
-restart gnome: sudo /etc/init.d/gdm start

If all went well, that should bring you back to the login screen.
Get that mastered then next we'll look for logs to give us some
insight.

---

### Post by vanadium on 2011-05-13
Try if disabling "Sync To VBlank" in CompizConfig Settings Manager helps. You may need to install it, because it is not installed by default (use Ubuntu Software Centre and search for Compizconfig, install "Advanced Desktop Effect settings"). In the left column, click "General", then "OpenGL" and turn of the option.

---

### Post by Jolicoeur on 2011-05-13
That partially worked.  I now can watch for several minuted or longer but if I move the mouse to make any adjustments like screen size it goes black again and I have to reboot.

---

### Post by vanadium on 2011-05-14
Another one to try:

Composite plugin: check "Undirect Fullscreen Windows". This would alleviate problems woth full screen video playbakc only.

Else, you will need to look into driver issues: I hope jtarin can continue to guide you for this direction.

---

### Post by jtarin on 2011-05-14
Menu>SystemTools>LogFileViewer.

---

