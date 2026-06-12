---
title: "HP TouchSmart tx2 64bit ATI HD3200 PROBLEMS"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Yojimbo1973 on 2009-09-11
[SIZE=2]I try to engage the Visual Effects in the Appearance Preferences, but I get the following message....
"Desktop Effects could not be enabled"

I went into terminal and did a "compiz", here are my results....but I do not know what to do next.[/SIZE]

[FONT=Book Antiqua][SIZE=2][COLOR=Navy]Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
[/COLOR][/SIZE][/FONT]:confused:

---

### Post by R3fr4cti0n on 2009-09-11
hey man, jsut go to system admin> synaptic and type compiz, thats the easyest way to install.

---

### Post by R3fr4cti0n on 2009-09-11
o and us tx2 users need to install drivers fot the ati.

---

### Post by Yojimbo1973 on 2009-09-11
> **R3fr4cti0n said:**
> o and us tx2 users need to install drivers fot the ati.


Thanks ey.....but I've been trying to install ati drivers all week.
I'm just not getting this...plus my sound just went too.
This is so frustrating.
Appreciate the help.

---

### Post by Yojimbo1973 on 2009-09-12
Used synaptic package manager......compiz.........reinstalled the drivers....still not working.

---

### Post by Favux on 2009-09-12
Hi Yojimbo1973,

I don't think you've ever said if you are using Jaunty or Karmic.  If Karmic I don't think the proprietary ATI drivers completely support it yet.

---

### Post by Yojimbo1973 on 2009-09-12
> **Favux said:**
> Hi Yojimbo1973,

I don't think you've ever said if you are using Jaunty or Karmic.  If Karmic I don't think the proprietary ATI drivers completely support it yet.

Jaunty......I finally got the effects going by downloading and installing the linux drivers from amd.
I did a few other upgrades.....but can not install the gnome desktop extras.

And for some reason.....MY SOUND IS GONE...........AGAIN!!!
Sheesh!

---

### Post by Favux on 2009-09-12
Hi Yojimbo1973,

What line are you adding to alsa-base.conf?

---

### Post by Yojimbo1973 on 2009-09-13
?......none?....I don't know...I lost track.......could it be driver conflict?
Newbie here!

---

### Post by Favux on 2009-09-13
Hi Yojimbo1973,

OK.  I'm assuming you have the HP TX2z tablet pc with the n-trig digitizer.  See "7) Sound" on this HOW TO here:  [http://ubuntuforums.org/showthread.php?p=7863677#post7863677](http://ubuntuforums.org/showthread.php?p=7863677#post7863677)

Hope this helps.

---

### Post by eramax on 2009-09-13
> **Yojimbo1973 said:**
> Jaunty......I finally got the effects going by downloading and installing the linux drivers from amd.
I did a few other upgrades.....but can not install the gnome desktop extras.

And for some reason.....MY SOUND IS GONE...........AGAIN!!!
Sheesh!

**could you put the links because i need them**

---

### Post by Yojimbo1973 on 2009-09-14
Thanks folks!
All fixed.
Now I went an screwed up my Firefox browser when I tryed to install the new version.
The browser wont start.
Shiretoko starts no problem though.
Very strange.

---

