---
title: "Change screen resolution?"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Benboom on 2009-05-08
I'm new to linux. I just installed 9.04 on an old Mac G4 and although the bootup process appears to happen with a reasonably high resolution display, when it finishes I'm left with 800x600. If I go into the System>Preferences>Display only two resolutions show up: 800x600 and 640x480 (I think that's the smaller one, I didn't try it). My monitor is a Sony Multiscan 17sfII which normally runs at 1024x768, 75hz on the same Mac. How can I get out of this cramped screen?

When I ran the Help program and put in "Display" I got a hit but the viewer stalled when I clicked on the link and I finally exited it a few minutes later with a still-spinning icon. So THAT didn't tell me much.

Thanks!

---

### Post by kdib on 2009-05-08
Hello,

Correct me if I'm wrong but mac is not supported. From what I gather (I'm not a mac user btw) you will have to wait for community developed solutions for support with Jaunty. Maybe try 8.10 and see how that goes? If you don't mind experimenting; maybe try an upgrade from there?

sorry I can't be more help...

---

### Post by Benboom on 2009-05-08
Okay, I will post in the Mac area; I thought this was probably a beginner-type question ("How do I change screen resolutions?") that pops up all the time, but I had already tried the obvious fixes (which worked with an earlier version of Ubuntu - whoops, make that Kubuntu).

---

### Post by CatKiller on 2009-05-09
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by Bartender on 2009-05-09
I just slapped a test PC together from old parts and have this exact problem.
Gonna take CatKiller's instructions out to the shop and see what happens.
Two questions - I understand the "cp" command.  You want to save a copy of the original xorg.  But what's the command to restore the original?

Also, in the vertical refresh field.  Do you need two values, or can you just enter one value for the screen's optimal refresh?

---

### Post by Didius Falco on 2009-05-09
If you want to keep the same refresh rate you could just enter the same value for both. Just be sure you know your monitor can handle it.

To restore the original, you'd just reverse the command, like so: ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```Not the capital X in X11 - linux is case-sensitive.

Regards,

Didius

---

### Post by Panzor on 2009-05-09
> **Bartender said:**
> I just slapped a test PC together from old parts and have this exact problem.
Gonna take CatKiller's instructions out to the shop and see what happens.
Two questions - I understand the "cp" command.  You want to save a copy of the original xorg.  But what's the command to restore the original?

Also, in the vertical refresh field.  Do you need two values, or can you just enter one value for the screen's optimal refresh?

To restore, just change the [source] and the [destination].

So, if the syntax is:```
cp [source] [destination]
``` to back up the file - ```
cp [destination] [source]
``` will restore that value. What you're looking for is ```
cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Also, to maybe answer the refresh range question - I've only seen it to be a range of values. If you *know* an exact value, I'd try putting a range with that value in the dead center. Couldn't hurt giving it a try :P.

EDIT: I was ninja'd! Post above is all you need to know :P

---

### Post by CatKiller on 2009-05-09
> **Bartender said:**
> Also, in the vertical refresh field.  Do you need two values, or can you just enter one value for the screen's optimal refresh?

You need two values.

A cursory Google gives
HorizSync 31-65
VertRefresh 50-120

EDIT to clarify: These are the values for Benboom's monitor. Bartender's will be different.

---

### Post by Bartender on 2009-05-09
OK, thanks -
I'm a coward when it comes to the command line.  But this test PC won't have any personal data so I can make a mess.
Cat's last post got me really confused.  I thought Horiz Sync would be the exact numbers the monitor wants, such as 1920-1200.  "31-65?"  What does that mean?

Hey, Benboom, sorry for hijacking your thread but maybe we can both learn?

---

### Post by CatKiller on 2009-05-09
> **Bartender said:**
> Cat's last post got me really confused.  I thought Horiz Sync would be the exact numbers the monitor wants, such as 1920-1200.  "31-65?"  What does that mean?

These aren't screen resolutions, they are refresh rates. There's all sorts about how monitor timing works on the Internet. The mechanism for moving the electron gun that displays an image can only go at certain speeds. It scans left-to-right and quickly back again for each line of the display, and top-to-bottom and quickly back again for each frame. The speed that the gun can move is a mechanical reality based on how the monitor is made, and the timing of the signal is critical for getting a coherent image. Each mode (certain resolution at a certain vertical refresh rate) will have different timings. These settings tell X how fast the gun can move to enable it to calculate which modes the monitor can do so that it can calculate the timings. Each mode will have a different speed for the vertical and horizontal scans. This range of values determines which speeds the monitor can do.

---

