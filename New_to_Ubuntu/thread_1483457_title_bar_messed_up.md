---
title: "title bar messed up"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by webwiller on 2010-05-14
Hi folks!
I upgraded ubuntu from 9.06"karmic Koala" to the last 10.04 "lucid". The problem I encounter sofar is about the 3 buttons (collapse, close and reduce to icon) I normally have on the top right of my title bar. They now moved to the top left and I'm not able to get them back to the right.

Any clue guys?
tx in advance!

WW.

---

### Post by mhgsys on 2010-05-14
hihi

Go to system> Preferences > Appearance 

And select a different theme

---

### Post by 2hot6ft2 on 2010-05-14
That's the way they made it in 10.04
> **bluelamp999 said:**
> ALT-F2 to fire up the Run dialogue control.

Type in ```
gconf-editor
``` and select Run, this will bring up the Configuration Editor...

Then apps>metacity>general and look for the *button_layout* parameter and change the value to ```
close,maximize,minimize:menu
```

Then you should have Mac style window controls...
> **Paul T. said:**
> Hi,

I had same concern about moving buttons, but easily fixed:

Open up a terminal, type "gconf-editor" then navigate to /apps/metacity/general and make the "button_layout"
Code:
:minimize,maximize,close

Got that from another user, worked for me :P
Basically just move the **:** to the other side

---

### Post by webwiller on 2010-05-15
With the mentioned workarounds I can change buttons order BUT they stick on the top left, I want to move them to the top right corner!

Did I do something wrong?

:-(

---

### Post by webwiller on 2010-05-15
In the end I just selected another theme and buttons moved to the right automatically! Don't know...but sorted, thx!

---

