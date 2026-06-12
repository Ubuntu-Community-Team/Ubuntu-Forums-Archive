---
title: "Horizontal Lines flying across on monitor"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-12-24
Hello.

I recently purchased a emachines E181H TFT LCD monitor for use with my ubuntu desktop. My screen adjusted appropriately to accommodate the new widescreen monitor, but the problem lies in the monitor itself. I get these weird sections on my monitor consisting of really fast-moving lines. I have no clue what is causing this... please help!

Thanks a lot!
Brad

---

### Post by Geoff918 on 2009-12-24
If it's not specific to Ubuntu (and it seems from your post you've eliminated that through some control) then what else is around your monitor?

Do you have speakers that may be throwing off radiation? Do you have a cell phone sitting nearby?

I know these things interfere with CRTs. I am not positive about the LCDs. I will try to research that.

---

### Post by Geoff918 on 2009-12-24
Actually, are the lines horizontal? Vertical? Random?

Are they more common during certain activities?

Is the cable physically well connected? Is it loose? Are there any pins or anything loose? Is the cord unbent (not bent up against a wall)? Is the cable wrapped around any power cords?

---

### Post by darkeye123 on 2009-12-24
I thought about that but my CRT monitor was sitting there not long ago... It wasn't affected by anything so It doesnt seem to be related.

---

### Post by darkeye123 on 2009-12-24
Well my cords are close together... but isnt that just the nature of a monitor... it has power cords + audio cables + vga cables close together. 

The lines are horizontal, but in columns running down the monitor...
Like this:

-  -  -  -  -  -  -
-  -  -  -  -  -  -
-  -  -  -  -  -  -

When looked at from the side, they form darker columns in comparison to the rest of the screen. 

The monitor lines are ever present, from the graphical login onward. No activity really brings them about, but on darker backgrounds they are less visible.

Weird.

---

### Post by Geoff918 on 2009-12-24
Is it truly not Ubuntu specific? If you booted into anything else do the lines still show? Do you have any other machine you can plug your monitor into as a test?

---

### Post by darkeye123 on 2009-12-24
Will test and report back in a bit.

---

### Post by sandyd on 2009-12-24
you may need to change the horizontal/vertical sync/refresh rate

---

### Post by darkeye123 on 2009-12-24
Just tested on the same computer... There are no lines in the bios or boot up (I have disabled the splash and quiet mode in grub) but as soon as gdm loads the lines appear. 

My monitor isn't recognized in the Display Settings, but my resolution and stuff still work fine. I can change the resolution back into 4:3 mode, etc., but I cannot change the actual refresh rate, which is stuck at 60 HZ. 

How would I change the vertical/horizontal refresh rates/sync?

---

### Post by darkeye123 on 2009-12-24
[LEFT]Other Weird stuff... I don't have a xorg.conf file in /etc/X11/

```

brad@brad-desktop:~$ cd /etc/X11
brad@brad-desktop:/etc/X11$ ls
app-defaults             fonts    X      Xresources  Xsession.options
cursors                  openbox  xinit  Xsession    XvMCConfig
default-display-manager  rgb.txt  xkb    Xsession.d  Xwrapper.config

```

I can't even find it...
```
brad@brad-desktop:/$ locate -i xorg.conf
/usr/share/man/man5/xorg.conf.5.gz

```


[/LEFT]

---

### Post by sandyd on 2009-12-25
by default, you dont. if you read the release notes, it tells you how to create it

---

