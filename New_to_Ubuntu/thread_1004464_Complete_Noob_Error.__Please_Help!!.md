---
title: "Complete Noob Error.  Please Help!!"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Aeana on 2008-12-07
Okay, I was trying to do some work on my project computer at university after having installed ubuntu.  I was following some instructions I found online to change some settings to do with Flightgear I pressed ctrl+alt+F6 as it told me to.

I was met with a black screen and was completely confused and didn't know what to do or how to get back to normal.  So I didn't mess anything up I wandered off down to the next computer lab to try to find a way to get back to my desktop.  However, by the time I returned the computer had been shut off by someone (they tend to do that :evil: ) and when I tried to restart it it comes up with missing operating system.  Is there any way I can recover the OS and all my settings?

Please help, I don't want to have to start from scratch! :(

---

### Post by lovelyvik293 on 2008-12-07
With the ctrl+alt+F6 you opened a new terminal of the OS.To come to the normal gui you can use the ctrl+alt+f7.

And i think that "SOMEONE" may edit the grub file,to check it please tell me what you get when you boot up.And how you know that OS is wiped off.

---

### Post by InfectedWithDrew on 2008-12-07
Searching the boards gave me this thread.

[http://ubuntuforums.org/showthread.php?t=969041](http://ubuntuforums.org/showthread.php?t=969041)

It seems that Ctrl-Alt-F6 will make your computer change to a black terminal display.  You were probably just panicking and when it turned black you flipped out, not waiting for the terminal to appear eventually (my guess, but I could be wrong).

Ctrl-Alt-F7 normally fixes this, it seems, but your error is very interesting (and also scary).  Perhaps you could try to use a Live CD to probe the computer?  (Though I'm not sure what would be wrong in there.)

---

### Post by Aeana on 2008-12-07
That's great thanks guys.

I was a bit freaked out when it came up with missing operating system.  If I boot it from the CD and press ctrl+alt+f7, will that work.  Or should I try this?

[QUOTE=Peter09]Go into recovery mode - hit ESC at GRub and select it.

Then try the reconfigure X option - good to start.

If this doesnot work, go to recovery mode and select the command shell and type startx.

Come back and tell us what happens.[/QUOTE]

---

### Post by pedrogfrancisco on 2008-12-07
Ok, first, those guys are right.

CTRL+ALT+F6 switched you to a terminal. CTRL+ALT+F7 would have, in that situation, gotten you back to your "normal" desktop.

Now if you now get a missing OS error on startup things are getting tricky. Tell us exactly what is the error message so we can further help you...

---

### Post by lovelyvik293 on 2008-12-07
Please post the error you got at boot time.

---

