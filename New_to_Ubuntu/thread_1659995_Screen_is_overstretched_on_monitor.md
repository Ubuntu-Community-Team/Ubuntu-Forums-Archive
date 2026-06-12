---
title: "Screen is overstretched on monitor"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Mr. Eggplant Man on 2011-01-04
It's only by a little bit, but my display on my monitor expands a little bit beyond the screen, how do I adjust it juuuuust right?

---

### Post by MechaMechanism on 2011-01-04
> **Mr. Eggplant Man said:**
> It's only by a little bit, but my display on my monitor expands a little bit beyond the screen, how do I adjust it juuuuust right?
CRT (boob tube) or LCD?  If it's CRT, then you need to use the controls on the monitor to underscan slightly the image.

---

### Post by Mr. Eggplant Man on 2011-01-04
I'm on an LCD moniter.

---

### Post by MechaMechanism on 2011-01-05
Whats the resolution of your display and whats the resolution the OS is set to.  As example, my display has a native resolution of 1680x1050 and Ubuntu is set to the same resolution.  Is your display an LCD computer monitor or an LCD TV display.  Mostly curious if you have the display output to match the LCD native resolution.

Run the following command and copy and paste the output here.  Run this in the terminal.  If your running Gnome then it's in the menu Applications/Accessories/Terminal
```
xrandr
```

---

### Post by Mr. Eggplant Man on 2011-01-05
From the command you gave me, I THINK I'm on a 1680 * 1050. So, should I go with 1280*1024? I was thinking that might be a little small. Also, I still don't know how to change it.

---

### Post by Dans564 on 2011-01-05
You def want to use the highest resolution your screen supports.  Otherwise quality will be shoty.  Try playing around with the buttons on the monitor itself, go through its menus and see if you can't figure it out.

---

### Post by Frogs Hair on 2011-01-05
Try system > preferences > monitors to find resolution settings. If you have installed Nvidia or ATI drivers , try system > administration Nvidia X server settings or the ATI counterpart.

---

### Post by Mr. Eggplant Man on 2011-01-05
I was at the highest (1680 * 1050), which looks normal, but is overstretched, then I tried 1280 * 1024, which is more overstretched, and blurry, and looks terrible. I don't know if resolution itself is the problem, but it's just too wide. It looks fine.

---

### Post by Frogs Hair on 2011-01-05
Try system > preferences > keyboard shortcuts and see if maximize windows is enabled  and press the key combination listed . On my configuration it is not enabled , but may on yours .

Check your monitors manual settings as suggested by Dans564 , it seems like your resolution is correct but you are toggled to full screen.

---

### Post by MartyBuntu on 2011-01-05
Would you tell us the make and model of the monitor?

---

### Post by Mr. Eggplant Man on 2011-01-05
It's a Dell.

---

### Post by MechaMechanism on 2011-01-06
The only thing I can think of is that your video card or display has overscan turned on.  Probably the LCD.  Do you use the LCD as an TV sometimes.  Some TV displays overscan the computer output by default.

Please attach here your x.org file using the attachment option for post.  xorg.conf can be found in /var/log.

Also post the complete output of
```
xrandr -q
```Don't tell me what you think, do post the entire ouput.

We need to try
```
xrandr --output DISPLAY NAME --set underscan off
```

---

