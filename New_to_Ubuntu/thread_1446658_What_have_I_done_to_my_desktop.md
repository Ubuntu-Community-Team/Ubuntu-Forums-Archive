---
title: "What have I done to my desktop?"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by Den-den on 2010-04-04
I struggle googling this 'glitch' to find a solution, can you suggest how to fix it please?
If you see the attachment it should become more clear. The area on the left, that takes 1/3 of the screen is not usable in any way. It looks like the margin has shifted right.
How can I fix this please, any ideas?

---

### Post by MooPi on 2010-04-04
I haven't a clue where to start so can you give us some details. System specs , recent updates , any changes you may have attempted ?

---

### Post by Den-den on 2010-04-04
Sure, here are my specs:
Samsung NC10, running latest Ubuntu 9.10.

The screen has shifted the margins after I connected it via VGA cable to my LCD TV. I tried reconnecting, but nothing seemed to have to work :(

I can use the panel and view webpages maximized, it is just the Desktop. The area on the left contains frames of graphics of any windows overlapping the area...

This has got to be something with the X server, or xorg :/ not sure honestly...

---

### Post by clive littlewood on 2010-04-04
Hi

Check preferences > monitors and make sure all the settings are correct.

I had that problem once connecting to a TV as a monitor, but everything reverted when I shutdown and restarted.

Clive

---

### Post by r-senior on 2010-04-04
I get something similar (but not quite so bad) if I connect my laptop to some presentation projectors mid-session. Three ideas to sort it out:

1. Reboot ;)

2. "Display Settings" -> "Detect Monitors", select correct resolution.

3. On a laptop, press the function key that's used for selecting external displays - maybe labelled CRT/LCD and usually a combination of "Fn" + "F5" or something similar.

---

### Post by Den-den on 2010-04-04
rebooted about 10+ times, and 'Display' settings seem to be set just right... :/
Nothing out of ordinary, really. I believe this should be (somewhere) adjusted in a config file where screen resolutions and any margins are defined, any ideas please?

---

### Post by arnab_das on 2010-04-04
do u have ur display drivers installed? as in system > administration > hardware drivers

---

### Post by Den-den on 2010-04-04
None, no propriety drivers, never needed any...

---

### Post by Linuxforall on 2010-04-04
Try this, boot without the monitor on and then when its fully booted turn the monitor on, you might see the resolutions all screwed up, don't worry, reboot but this time normally with the monitor on and see if the issue goes away, sometimes the EDID is not read correctly and these issues crop up, doing this procedure resets the EDID.

---

### Post by Den-den on 2010-04-04
> **Linuxforall said:**
> Try this, boot without the monitor on and then when its fully booted turn the monitor on, you might see the resolutions all screwed up, don't worry, reboot but this time normally with the monitor on and see if the issue goes away, sometimes the EDID is not read correctly and these issues crop up, doing this procedure resets the EDID.

Gave that a go but no lock :(

HOWEVER, i tried logging out and logging in with failsafe Gnome session. The problem 'resolved' as the background and Desktop was right in place. Also tried creating a new user, and there was no faults too. The problems has to to be somewhere in a config file under ~/.

---

### Post by arnab_das on 2010-04-04
> **Den-den said:**
> None, no propriety drivers, never needed any...

i'm not sure but u might wanna try and give it a go. if u dont want to keep a proprietary driver, u can always remove it.

---

