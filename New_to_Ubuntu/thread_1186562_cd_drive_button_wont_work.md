---
title: "cd drive button wont work"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by hyperhopper on 2009-06-13
whenever i use linux, i always just use eject /dev/scd0 to eject discs, but my sister wants to be able to just press the button to eject it.. how can i make the button work consistently?

---

### Post by Celauran on 2009-06-13
Unless my memory is bad, the tray remains locked until the disc is unmounted. Once unmounted, you should be able to use the button normally.

EDIT: Just tested it. Doesn't work like that any more.

---

### Post by hyperhopper on 2009-06-13
is there any way to make pressing the button auto-de-mount, then open??

---

### Post by Crunchy the Headcrab on 2009-06-13
I had similar problems on my laptop until I set my optical drive to compatibility mode in bios.  Previously it was set to SATA.  This probably isn't even related because I was having a host of other problems with my cdrw/dvdrw drive until I did that.

---

### Post by Silentvoice on 2009-06-24
I have this problem too, I'm on Xubuntu 9.04.

It's almost never an issue, but it is troublesome with multi-cd installs where I can't alt-tab out of the window in order to eject via the eject program.

The way I fixed that was by binding eject to a keyboard key I never use, in my case scroll lock.

to do this

Applications-->Settings-->Keyboard-->Applications Shortcuts-->Add

the command is

```
eject /dev/cdrom 
```

my device mounts to /dev/cdrom at least, I don't know if this changes from computer to computer.

---

### Post by Lorin Ricker on 2009-06-29
Thanks to this thread, I've learned the **eject** command... Useful because my CDROM drive has a physically recessed button which is cantankerous and sluggish to push/respond; that, plus I have to get up out of my chair, because my box is on top of my roll-top desk, just out-of-reach.  Thank you!

"eject -h" shows the capital **-T** option, which *toggles* the CD-ROM tray open/close.  This suggests the following alias (use the device form which works best for you):

```
$ alias ej="eject -T /media/cdrom"
$ ej
$ ej
$ ...   # CD-ROM tray now opens and closes, and I don't have to get up!

```Cool -- now to just put this into a button for a desktop toolbar, might just be perfect.

---

### Post by Lorin Ricker on 2009-06-29
And the desktop toolbar widget is embarrassingly trivial to implement:

1. Right-click on a toolbar, choose "+ Add to Panel..."

2. Select "Custom Application Launcher" (right at the top of the list), click on "+Add" button

3. In "Create Launcher" dialog box, fill-in appropriate descriptions for "Name:" and "Comment:" fields (if you like), and in "Command:", enter the same com-line as used for the alias command: "eject -T /media/cdrom"

4. Click on the default icon (the spring-launcher thingie) if you want to select a different, identifiable icon, then "OK" to close...

Now, happily click your button to open/close your tray.  Way cool (or I'm way too easily amused).:guitar:

---

### Post by mystmaiden on 2009-07-10
I had the same problem it was making me crazy - nothing helped until I opened up the machine. The culprit - a tiny little dust bunny. I wish everything was that easy. :)

myst

---

