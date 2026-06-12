---
title: "Trying to set up an external display for my laptop"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by scubabuddy on 2009-01-13
hey, i'm a linux noob. i've been running hardy heron for about 3 months but i've been avoiding all the technical stuff... until now

My laptop is a sony vaio sz440, nvidia chipset i believe.

I got a 22" flat screen at an incredible price and i would really like to set it up. The first thing i tried was nvidia-settings and that detected the monitor as a crt, with a maximum resolution of 640 x 480. Its native resolution is 1680 x 1050. I attempted to manually edit my xorg.conf but i got an error when i tried to save it. It said i didn't have access.

Help? I have no idea what i'm doing :lol:

---

### Post by abn91c on 2009-01-13
you have to use the sudo command for root access. First try in the monitor settings if you get a list of available monitor brands, use [COLOR="Red"]**Generic monitor**[/COLOR] then select the lcd monitor size is closely matches yours.

---

### Post by scubabuddy on 2009-01-14
by monitor settings, what were you referring to? nvidia-settings or ubuntu's screen resolution stuff or what? sorry to be stupid but i just don't know :D

um, strangely enough, i just tried a different VGA cable and it recognized the monitor just fine as the monitor that it is at a resolution of 1680 x 1050. It's set up right now as Twinview but i'd like to have them as separate x screens. nvidia-settings is now throwing an error when i try to save the x file. It fails to create a backup. 

Any ideas? 'cause i sure don't have any :idea:

---

### Post by bodhi.zazen on 2009-01-14
Run nvidia settings with root power :

```
gksu nvidia-settings
```

Then when saving your settings, when you click the "Save to X Configuration File" a second dialog box comes up.

Deselect (uncheck) the "Merge with existing file" box, then hit "Save".

---

### Post by scubabuddy on 2009-01-14
> **bodhi.zazen said:**
> Run nvidia settings with root power :

```
gksu nvidia-settings
```

Then when saving your settings, when you click the "Save to X Configuration File" a second dialog box comes up.

Deselect (uncheck) the "Merge with existing file" box, then hit "Save".

thank you. that solved that.

however, there are new issues:
1) my external has i higher resolution than my laptop screen. I set it to this higher resolution before i saved the x config file. when i restarted X, it reverted to the lower resolution of the laptop screen. edit: this seems to have fixed itself after a full system reboot

2) My external somehow made itself Xscreen 0 and my laptop screen is Xscren 1. I need this to be the other way.

3) Now i'm getting an Nvidia splash screen before the ubuntu login window that i've never seen before. is that an issue?

thanks so much for all your help so far :D

---

### Post by bodhi.zazen on 2009-01-14
You should be able to make all those changes in nvidia-settings (I hope).

The logo is "normal" and you can disable it if you wish (most people do).

---

### Post by scubabuddy on 2009-01-15
The only thing i can't find a way to change is which display functions as the primary. that's ok though, it's not causing me any problems.

Thanks for all your help guys.

---

