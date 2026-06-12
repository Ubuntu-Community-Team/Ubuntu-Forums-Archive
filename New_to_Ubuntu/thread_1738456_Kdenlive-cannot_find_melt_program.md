---
title: "Kdenlive-cannot find melt program?"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by xpaperbackwriterx on 2011-04-24
So I've been doing an english project and its been going swell. Every once in a while I render it to a file so I can see it without all the glitchiness of the preview window.  I tried to do it just now and all of a sudden it says "Cannot find the melt program required for rendering (part of MLT)". O.o I have not a clue what that means but I'm good at following instructions soooo.....help?

---

### Post by rosencrantz on 2011-04-24
Did you install melt? (sudo apt-get install melt or with Synaptic)

---

### Post by xpaperbackwriterx on 2011-04-24
I think I did, or else it wouldnt have been rendering before....but I'll install it anyways....

---

### Post by xpaperbackwriterx on 2011-04-24
*sigh* still same messege

---

### Post by xpaperbackwriterx on 2011-04-24
so on the recomendation of a guy from another forum, I uninstalled completely and reinstalled, and now it wont open and says "Project profile was not found, using default profile." *headdesk* *headdesk* *headdesk*

---

### Post by rosencrantz on 2011-04-25
What won't open, Kdenlive or melt?
I checked the config file, ~/.kde/share/config/kdenliverc
The paths to external programs are in the [env] section, see whether they are correct. Mine looks like this:
```
[env]defaultaudioapp=/usr/bin/audacity
defaultimageapp=/usr/bin/gimp
defaultplayerapp=dragon
mltpath[$e]=/usr/share/mlt/profiles/
rendererpath[$e]=/usr/bin/melt
```
I haven't used Kdenlive recently, so I can't say whether this works.
If some app complains about missing or wrong configuration data, it's always worth a try renaming the config files/directories (like kdenliverc.backup) and let the program write a fresh file with default settings.

---

### Post by xpaperbackwriterx on 2011-04-25
Kdenlive.

*blinks* ...I'm terribly sorry, but I have almost no idea what you just said. I'm smart enough to work my way around but not that savvy yet. (I just haven't had time yet.)

---

### Post by rosencrantz on 2011-04-25
Sorry ;-) I'll try to be more detailed (it's hard to judge what people are used to and how well they know their system in this forum ...)

Usually, when a program has startup problems (after having worked OK previously), it isn't the fault of the executable itself, but of the configuration files. Those are saved (hidden) somewhere in the user's home directory and aren't replaced when you re-install the executable.
The only config file for Kdenlive I found is ~/.kde/share/config/kdenliverc
(Alt+. in Dolphin or Konqueror will toggle the display of hidden files, ~ is the common shorthand for your home directory).
If Kdenlive doesn't start up, I'd try renaming this file or moving it somewhere else, so Kdenlive won't find it when it tries to read in your configuration. Kdenlive will then create a new kdenliverc file with the default settings (and, if you're lucky, the correct paths for melt).
If you open kdenliverc, you'll find the section I copied somewhere in the file. Kdenlive looks for melt etc. at the locations specified there, like /usr/bin/melt. So, if it still can't find melt, I'd compare the kdenliverc settings to the actual location of melt on your system, which you can find out by typing [FONT="Courier New"]which melt [/FONT]in a terminal.
If this doesn't get you any further, try opening a terminal and typing [FONT="Courier New"]kdenlive[/FONT]. This will start Kdenlive's graphical interface, but also display potential error messages in the terminal window.

---

### Post by beew on 2011-04-25
Which version of  libmlt and kdenlive do you have? Which repo did you install them from? There was a problem with the version in sunab's ppa version of kdenlive and libmlt versions from different sources.
The problem was resolved in yesterday's update (kdenlive version 8 and libmlt4)

---

### Post by xpaperbackwriterx on 2011-04-25
rosencratz: I renamed it and it worked! Thank you very much for your detailed instructions ^.^

beew: obviously my problem is fixed, but I'll tell you anyways. Kdenlive: 0.7.7, libmlt: 0.5.7 (i think). I got it from the software center, that's all I know.

---

