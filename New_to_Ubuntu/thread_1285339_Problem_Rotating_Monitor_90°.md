---
title: "Problem Rotating Monitor 90°"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by shy_guest on 2009-10-07
I am running Jaunty on a Sony Vaio laptop.

I just got an Iiyama 24 inch 16:10 1920x1080 monitor.

I wanted to rotate the monitor 90° & (if possible) NOT rotate the laptop. 

I used Display in the System Preference menu to rotate both.

I then did something in that menu (not too sure what) & was asked if I wanted automatic detection of virtual something ??? It was stated that this was recommended so I clicked on yes. I was asked for my system password & gave it & some change was then carried out.

Now my laptop screen has a black border on each side while the monitor picture stretches to fill all the screen.

The choices to rotate the display 90° right or left have disappeared, leaving only the choice to turn it upside down ! It would be nice to improve screen resolution from 1024x768 too if that's possible but the options are in a dropdown list with no higher resolution.

How can I do what I want - rotate the monitor 90° & (if possible) NOT rotate the laptop - or else restore the original settings so I can at least rotate them both ?

---

### Post by gali98 on 2009-10-09
What video card do you have?
You can run:

xrandr -o right
xrandr -o left
xrandr -o normal
or
xrandr -o inverted
to rotate the display. Just run it in the terminal.
Kory

---

