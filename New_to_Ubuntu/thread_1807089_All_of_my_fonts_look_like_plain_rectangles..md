---
title: "All of my fonts look like plain rectangles."
date: 2011-07-18
forum: New to Ubuntu
---

### Post by flipNasty on 2011-07-18
Yesterday, I installed FontMatrix, and now my whole computer is in boxes... I've attached a screenshot of the problem, but I'm kind of at a loss as to what to do to make it right... has anyone seen this before?

---

### Post by LowSky on 2011-07-18
I guess for know you will need to do things by sight

Go to appearance... the icon looks like a shirt and tie. using the normal ubuntu theme, you could also right click and the last option is to change the wallpaper and pick the last option to get there too.

the last tab is fonts, you should be able to switch them there.

if not things will be complicated, you may need to log switch into another console to fix things. Hopefully real letters will appear there.

---

### Post by Brushstroke on 2011-07-18
Hmm. Open a Terminal and "blindly" type: 

```
sudo apt-get purge fontmatrix
```And then reboot. See if that helps?

---

### Post by flipNasty on 2011-07-18
So what had happened was I was using Font Matrix to manage my fonts, then I changed the name of my font directory from "Fonts" to "fonts".

I fixed it by using a virtual machine to ssh my way into my broken one and uninstalling Font Matrix:

```
sudo apt-get purge fontmatrix
```

Then I rebuilt the font index to get my old fonts back:

```
sudo fc-cache -fv
```

Then I reinstalled Font Matrix:

```
sudo apt-get install fontmatrix
```

And now my computer is back to Helvetica instead of boxes... Thanks for your responses! :KS

---

