---
title: "Switching between desks with mouse wheel ?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Innernet on 2009-11-03
Just got into 9.10 after using 7.10, which is able to select the other 'desk' surface by turning the mouse wheel while pointing a blank area on a desk.
Also, dragging a window beyond the frame border did move such to the other desk.

Cannot find how to enable/select the same action on 9.10.  Please, illuminate me ;)

---

### Post by quinnten83 on 2009-11-03
if you are running compiz (if you have nice minimize animations and shadows around the borders) you can install compiz-config-settings-manager and enable it there (something about viewports)
```

sudo apt-get install simple-ccsm
```

---

### Post by Innernet on 2009-11-03
Thanks for responding.  No animations nor shadows, I do not even know what compiz is.:cry:

---

### Post by realzippy on 2009-11-03
right click backround,backround settings,visual effects,enabled?

---

### Post by Innernet on 2009-11-03
Right clicking a desk background does not show the options you mention :cry:

---

### Post by realzippy on 2009-11-03
the last one.Sorry,not using english desktop ;-)

---

### Post by Cuddles McKitten on 2009-11-03
Run the Configuration Editor (or via terminal "gconf-editor")

apps -> compiz -> plugins -> vpswitch -> allscreens -> options

Change "next_button" to "Button5" and "prev_button" to "Button4"  Assuming you've got the default settings for Ubuntu (and they all work), that should let you switch workspaces with the mouse wheel.

If not, then ditch Metacity and get Openbox. :)

---

### Post by realzippy on 2009-11-03
Hm,wait.You said no word about cube..are you talking about the 2 desktops or
did you use compiz or beryl 3D Desktop (Cube) on Edgy and not know how to enable mouserotate?
"...the other desk" means no compiz question.2 desks.I forgot about those 2D desktops...

If you can see the 2 desktops,right click on them to configurate behaviour..

---

### Post by realzippy on 2009-11-03
*"If not, then ditch Metacity and get Openbox"*


lol

---

### Post by rkham11 on 2009-11-03
Thanks, Cuddles McKitten. I had the same problem and your solution worked!

---

### Post by Innernet on 2009-11-03
McKitten:   Followed you precise instructions with no success after setting Button5 and Button4.

To "ditch Metacity and get Openbox" I have no brains on how to do it, what they are for, plus fear of screwing something up.

Zippy:  No clue what Cube, Compiz, Beryl are.
In the bottom right I see the two 'desk icons' ; I can click select which 'desk' shows in my single monitor, but cannot select the swap by the mouse wheel nor drag a window shown in one 'desk' to the other 'desk' as in 7.10

:cry:

---

### Post by mangurt on 2009-11-03
Run this in terminal:

```

sudo apt-get install simple-ccsm
```


After you install simple-ccsm, click on system, preferences,simple-Compizconfig Settings Manager

Select Desktop, select cube, desktops, 4, then click on edges, and click on the left and right edges.

---

### Post by Innernet on 2009-11-03
Thanks mangurt.
Done per your instructions, Cold reboot too just in case.  No change.
I assume the selection of "4" would make it four sidescrolling virtual desks instead of two I was after (even better) 
:cry:

---

