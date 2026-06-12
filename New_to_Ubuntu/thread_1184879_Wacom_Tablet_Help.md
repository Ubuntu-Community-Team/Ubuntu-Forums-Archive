---
title: "Wacom Tablet Help"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Turtleman on 2009-06-11
Alright, so I got a fresh install of 9.04, because last time I messed up my wacom config (and some other things eheheh). Anyways, Jaunty detects my wacom bamboo fine, and it is working. What I wanna know though is how I configure things such as pressure sensitivity and the eraser, or the buttons on the tablet. I installed wacom tools but I have no idea what that does, and when I run the wacomcpl command it doesn't show my tablet on the list. Can somebody explain how do I configure this thing? Also, I am able to use the command line decently enough.

---

### Post by Favux on 2009-06-11
Hi Turtleman,

Wacom-tools has wacomcpl among other things.  What I'm about to tell you to do has worked for a bunch of Bamboo users.

First the default 10-wacom.fdi is not parsing the device names correctly and that's why wacomcpl doesn't work.  To see this enter in a terminal:
```
xsetwacom list
```
That should return the linuxwacom names like stylus, eraser, cursor, and pad.  If it is blank that's why wacomcpl won't work.  To see what names HAL is returning enter:
```
xinput --list
```
To fix this do the following in order.  You will need to change the 10-wacom.fdi to one that does parse the names correctly.  So go to post #176 here and follow the directions:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)
Then to set up wacomcpl in Jaunty see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)
For additional info. on how to set up the Bamboo see shatterblasts post #188 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=19](http://ubuntuforums.org/showthread.php?t=967147&page=19)
And then to set up Gimp look at the Wacom wiki near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

That should get you set up.  Good luck!

---

### Post by Turtleman on 2009-06-11
Thanks Favux! It worked very well! You're the pen tablet god!

---

