---
title: "Compiz and OS X like questions"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Steve05TSX on 2008-12-25
Finally got Ubuntu 8.10 installed! I had a little difficulty getting the video to work (8600m GT) but now everything is running great.  

Had a few simple questions, is there anything out there similar to OS X where I could press F10 and all of the windows would show up in the screen and I can roll my mouse over it and release the button and it selects it?

also, I installed Compiz and it appears to be working (effects are in place) but it wouldn't let me customize them, gave me some sort of error.  Now I can't even find it anywhere in applications to even find out what the error message was

Thanks

---

### Post by nhasian on 2008-12-25
yes compiz is installed by default but the configuration manager must be installed manually.  from a terminal type

```
sudo apt-get install compizconfig-settings-manager
```

then you can customize things like animations and enable the desktop cube, etc.

for a fancy way to switch between apps using compiz hold down the superkey+tab.  also you can see all your desktops with superkey+e.

---

### Post by Steve05TSX on 2008-12-25
> **nhasian said:**
> yes compiz is installed by default but the configuration manager must be installed manually.  from a terminal type

```
sudo apt-get install compizconfig-settings-manager
```

then you can customize things like animations and enable the desktop cube, etc.

for a fancy way to switch between apps using compiz hold down the superkey+tab.  also you can see all your desktops with superkey+e.

that was the trick, now it's time to try to figure it out, so many options.  I remember the one I used before being a little bit simpler, this thing has too many options :confused:

---

### Post by nhasian on 2008-12-25
oh and i think I found the command you were looking for.  

Show All Windows (Scale) <Alt><Shift>Up

i'm sure you can bind it to another key like F10 if you like.

[http://wiki.compiz-fusion.org/CommonKeyboardShortcuts](http://wiki.compiz-fusion.org/CommonKeyboardShortcuts)

---

### Post by Steve05TSX on 2008-12-25
> **nhasian said:**
> oh and i think I found the command you were looking for.  

Show All Windows (Scale) <Alt><Shift>Up

i'm sure you can bind it to another key like F10 if you like.

[http://wiki.compiz-fusion.org/CommonKeyboardShortcuts](http://wiki.compiz-fusion.org/CommonKeyboardShortcuts)

awesome!!! thank you

---

### Post by Steve05TSX on 2008-12-25
ugh, that's exactly what I'm looking for, got a key binded for it and it's glitched or I'm doing something wrong.  It almost plays some games with me.  When I highlight over the window I want to select it moves away from me or switches sides :(

---

### Post by nhasian on 2008-12-25
wow i'm finding some real cool stuff with compiz now.  I went to CompizConfig Settings Manager->Windows management->Scale then I enabled the *Initiate Window Picker* by moving the mouse to a corner of my screen.  thats a lot easier than having to push <Alt><Shift>Up.

---

