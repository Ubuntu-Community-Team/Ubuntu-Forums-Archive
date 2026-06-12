---
title: "how do I get my second monitor working???"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by rocka on 2009-01-22
Hi,

I have had a video card with two DVI outputs for a while now, and today I got my second monitor back from repair after a long time [and a long story...]

How do I make Ubuntu recognize it?
It works at boot up time as it's going through the BIOS POST etc, so I know it's connected ok and the video card is talking to the monitor alright.

I went to System>Administration>Nvidia Xserver Settings and the second display is disabled. If I click on "Configure" and select "Separate X screen" then the display appears in the little layout window. But then even after rebooting, there is still no second display, and back in that same settings it's disabled again.

If I try to click on "Save To X Configuration File" I get the following error message:
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.



Any ideas?

---

### Post by overdrank on 2009-01-22
> **rocka said:**
> Hi,

I have had a video card with two DVI outputs for a while now, and today I got my second monitor back from repair after a long time [and a long story...]

How do I make Ubuntu recognize it?
It works at boot up time as it's going through the BIOS POST etc, so I know it's connected ok and the video card is talking to the monitor alright.

I went to System>Administration>Nvidia Xserver Settings and the second display is disabled. If I click on "Configure" and select "Separate X screen" then the display appears in the little layout window. But then even after rebooting, there is still no second display, and back in that same settings it's disabled again.

If I try to click on "Save To X Configuration File" I get the following error message:
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.



Any ideas?

Have you tried ```
gksu nvidia-settings
```

---

### Post by cyberfin on 2009-01-22
Hi there,

Your best bet is to do the following from terminal:

```
sudo nvidia-settings
```

...and configure the screen as separate. Click apply to check that it worked and if it did, then click on save to X configuration file.

This way, because you're accessing as administrator, it will allow you to save the setting and keep it for reboot.

Hope it helps.

EDIT: Damn. overdrank beat me to it :P

---

### Post by rocka on 2009-01-22
Hi,
thanks for the replies, guys.

So that worked, as far as now the two monitors start up and I have the wallpaper on both of them. And there is a menu bar at the top and a status(?) bar at the bottom of each screen.

But now, how do I actually use it???
Even if I open a new program from the menu bar on the second monitor, it opens the program on the first monitor. And if I try to drag the program across to the other monitor with the bar at the top of the program, it gets to the right edge of the first monitor then jumps to the second desktop on that same monitor.

I want to be able to have, say, web browser window on one monitor and spreadsheet on the other one. Or, one big spreadsheet across both monitors.

Thanks again for your help, tips...

cheers,

---

### Post by rocka on 2009-01-22
Hi again....
it's a little more complicated than I thought.

Trying a few further things, I find that only the file browser will only open in the first monitor. I can open movie player and a terminal window on the second monitor just fine. But here's the weird part:
If I open a spreadsheet on the second monitor, then open the  word processor, they will both open on the monitor the first one was opened on.

So that seems to mean that I can't have a spreadsheet on one monitor and a word document on the other.

Is that how it's supposed to be???

---

### Post by overdrank on 2009-01-22
> **rocka said:**
> Hi again....
it's a little more complicated than I thought.

Trying a few further things, I find that only the file browser will only open in the first monitor. I can open movie player and a terminal window on the second monitor just fine. But here's the weird part:
If I open a spreadsheet on the second monitor, then open the  word processor, they will both open on the monitor the first one was opened on.

So that seems to mean that I can't have a spreadsheet on one monitor and a word document on the other.

Is that how it's supposed to be???

I have no experience with separate x, I use twin view. You may try it. :)

---

### Post by stchman on 2009-01-22
Yes you have to run nvidia-settings as sudo so the application can modify your xorg.conf file.

---

### Post by cyberfin on 2009-01-22
overdrank is right on the monay gain. It sounds like you want to use Twinview. This will allow you to drag windows and in theory will also remember to which monitor you dragged it so when re-opening the application, it should open in the same place.

Good luck.

---

### Post by Paqman on 2009-01-22
> **cyberfin said:**
> It sounds like you want to use Twinview. 

+1

Twinview puts both monitors on one really wide desktop. You move your apps to whichever window you like.

---

### Post by cerealtx on 2009-01-22
not meaning to shoot a dead horse but yah but 2 seperate xservers seriously degrades performance because it takes alot to run both of them, i run TwinView and works just fine, u can play with the settings and what not to have the taskbars on just one screen or on both

---

