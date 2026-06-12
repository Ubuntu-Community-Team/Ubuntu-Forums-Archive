---
title: "Xorg crashed on me!"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Sugi on 2009-11-14
I need some help, I think my xorg or gnome is failing on me.  Every time I boot up, I get my nvidia logo, and log in screen.  I log in, and then my screen turns black and stays like that.

BUT I can move the mouse around, even though I can't see anything, but black. None of gnome hotkeys work (ALT+F1).  But I can indeed access the console (Ctrl+ALT+F4).  I have tried reverting back to an old copy of the xorg, but that doesn't work.

So my guess is gnome is failing or the xorg.  How should I fix this?

SPECS:
Ubuntu 9.04
Nvidia Card & drivers

Thanks,
Sugi


FIXED:

> **Sugi said:**
> 
But at the moment for some reason it's working now.  The last thing I did was failsafe gnome and went to "Nvidia X Server Settings".  Copy the xorg.conf settings from there and pasted it into my own xorg.conf file.  It worked after that.  Note, I did this many times before, sometimes it did not even show my monitor.  So I am kinda clueless why it just started working out of the blue.  I ended up making a backup of it for future use.

---

### Post by SkyNet2029 on 2009-11-14
you could try resetting your xorg.conf settings, like this:

pop into a virtual terminal (ctrl+alt+f4)

then do 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to reset the xserver configuration.

hope this helps

---

### Post by Sugi on 2009-11-14
Sorry, I forgot to include that.

I have tried the following:
sudo dpkg-reconfigure -phigh xserver-xorg
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig
None of these worked for me.  I still get a black screen after log in.  Though I can access failsafe gnome, but I can't use that for normal usage.

Sugi

---

### Post by falconindy on 2009-11-14
`Xorg -configure` is the new way to reconfigure xorg.conf. However, if you haven't changed it, resetting it to the defaults may not help. Is there anything relevant in /var/log/Xorg.0.log?

You could also try booting without an xorg.conf (rename it, don't delete it) at all just to see if you can log in that way.

---

### Post by Sugi on 2009-11-14
'Xorg-configure' doesn't work.  Maybe you misspelled the command?  I have a bunch of files in the log directly with Xorg_____.  Can I just replace them with the xorg.conf in the /etc/X11/ ?

Sugi

---

### Post by falconindy on 2009-11-14
> **Sugi said:**
> 'Xorg-configure' doesn't work.  Maybe you misspelled the command?  I have a bunch of files in the log directly with Xorg_____.  Can I just replace them with the xorg.conf in the /etc/X11/ ?

Sugi
Please re-read my post carefully. I didn't misspell it.

---

### Post by Sugi on 2009-11-14
falconindy, 'Xorg-confgiure' did not work for me.  I tried it couple of times and nothing happen.  I am not sure if it's linked to only 9.10, because I am on 9.04.   

But at the moment for some reason it's working now.  The last thing I did was failsafe gnome and went to "Nvidia X Server Settings".  Copy the xorg.conf settings from there and pasted it into my own xorg.conf file.  It worked after that.  Note, I did this many times before, sometimes it did not even show my monitor.  So I am kinda clueless why it just started working out of the blue.  I ended up making a backup of it for future use.

Thanks everyone for the tips.

Sugi

---

### Post by falconindy on 2009-11-14
> `Xorg -configure` is the new way to reconfigure xorg.conf.
> 'Xorg-confgiure' did not work for me.
See a difference? It's not the backticks versus single quotes.

---

