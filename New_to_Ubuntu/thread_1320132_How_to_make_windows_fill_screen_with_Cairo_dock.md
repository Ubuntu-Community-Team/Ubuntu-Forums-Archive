---
title: "How to make windows fill screen with Cairo dock?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by halo45121 on 2009-11-08
Hey. I have Cairo Dock installed so it sits at the bottom. When a window is maximized, it will not fill up the entire screen, it leaves an area for cairo dock at the bottom. It is kind of annoying me for some reason that there is so much empty space at the bottom. So how would I make the window fill up the screen when maximized? And I would also want to make it so that Cairo dock is always shown above other windows.

Thanks!


Matt

---

### Post by fabounet on 2009-11-09
go to the Accessibility module ;-)

to make the dock always shown above other windows, launch it with cairo-dock --keep-above, I personnally prefer the opposite solution (keep it under below other windows, in the Accessibility module again)

---

### Post by lavinog on 2009-11-09
behavior>Accessibility> uncheck 'reserve space at edge of screen for dock'

---

### Post by hossdozero on 2009-11-09
you'll also want to check *quick hide on fullscreen* and *quick hide on maximize* otherwise the dock will overlap maximized and fullscreen windows.

Also,you might wish to get rid of the top panel. To do this open a terminal and type 

```
gconf-editor
```

and navigate to: desktop > gnome > session > required_components, and change the panel field to: cairo-dock

then restart X

---

### Post by karatedog on 2010-02-10
If I put cairo-dock to the bottom, and set "prevent windows from overlapping the dock", then every maximized window will loose a few pixel from their bottom part.
Is this problem configurable?

---

### Post by kenbuntu75 on 2010-05-20
USING: UBUNTU 10.04  

:popcorn:

BG: Today is 5/20/2010. I've had CairoDock for a while and just tweaked the settings for the first time ever. I have a fully upgraded system.

OOPS: I suddenly found that full screen for apps does not cover the dock. I do not want that to happen.

SUCCESS: right click on the CairoDock, and get the option menu, then choose: Cairo Dock > Configure > set mode by using button in bottom-most leftside area of the window.

for advanced mode: Behavior (on left) > Visibilty (click the icon, rightside pane) > New screen appears, at top - "Visibility of main dock" >> choose "Keep dock below windows" from drop down box.

for simple mode: Behavior Tab(leftmost top) > Visibility of MAIN DOCK(2nd box down) >> choose "Keep dock below windows" OR "automatically hide the dock" from drop down box  

END

---

