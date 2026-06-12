---
title: "xinit from shell - no display"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by ValdeEdius on 2011-03-14
So I start into a shell, run xinit or startx and it appears to run the xserver just fine, but my monitor goes all blue and tells me theres no signal. My monitor reports that the shell is running at 1024x768@60Hz but I am guessing that is not what X is trying to use. I am able to press CTRL+ALT+F2 to go into another shell and type init 3 to halt the xserver and then go back to the first shell and press CTRL+C to kill the xserver that is halted.

How can I go about finding out how to properly launch the xserver? I tried launching with various dpi settings by doing the following
```
xinit -- -dpi 100
xinit -- -dpi 75
``` but neither of those worked and I felt I was going in the wrong direction with that idea.

---

### Post by TeoBigusGeekus on 2011-03-15
Instead of xinit, try
```
gnome-session
```

---

### Post by ValdeEdius on 2011-03-15
That was a valiant effort but did not work, unfortunately. I am almost certain this is an issue with the refresh rate. I am using a TV as a monitor and I have had this problem on some windows games that attempt to use too high a refresh rate (or too high a resolution) and I will have to manually change it.

---

