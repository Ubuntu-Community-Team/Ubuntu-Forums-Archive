---
title: "Another Inspiron 1100 problem"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Crimm237 on 2009-09-03
Yes yes, more nubs with issues dealing will the Dell Inspiron 1100, oh joy. I'm trying to switch over from XP to Ubuntu on an Inspiron 1100. I'm not too sure what the issue is though I am new to Linux and Ubuntu both so I've been shooting in the dark and have shoot myself in the foot more then once on this.   

The issue is that I've ran the live CD on the computer before and it loads fine asides one thing. I have my desktop tool bars but no desktop or icons. Then I restart the computer and boot up the Live CD and then it doesn't even load that I just look at a black screen. A brief error message pops up but then goes away before I even have a chance to read it.

I tried installing Ubuntu with an official copy of the CD and it did the same thing. It installed fine, loaded up fine asides the desktop Had my tool bars and everything on them worked fine. Turned it off ans restarted it. Nothing but a black screen ever time since. Anyone have any ideas? 

And sorry to have to ask this but if there is a fix to this I'll probably need some good instruction on how to do it. I don't know witch way is up down or any other direction in Ubuntu.

Thanks for your time and help.

---

### Post by LewRockwell on 2009-09-03
many times OEM series numbers will have quite a variation in internal components

with that in mind you may want to use windows to get your system information specifics to post here

also, it would be nice to know which Ubuntu you're working with

.

---

### Post by Sealbhach on 2009-09-03
When you get to the black screen, press Ctrl+Alt+F1 or F2, it doesn't matter as long as you get a login prompt. Log in, then run this command:
```

 sudo dpkg-reconfigure xserver-xorg
```

Have a look at this guide here, it will tell you what to do:

[http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

This may not fix your problem but it's the first thing to try.

.

---

### Post by Crimm237 on 2009-09-03
So I tried the Ctrl+Alt+F1 or F2. But that didn't do anything I was still staring at a black screen. And as it comes to the OEM series numbers I don't even have a clue. Forgive me but I kind of need point blank directions.

---

