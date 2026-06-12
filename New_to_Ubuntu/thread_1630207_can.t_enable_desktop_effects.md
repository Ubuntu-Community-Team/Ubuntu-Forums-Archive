---
title: "can.t enable desktop effects"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by owners4life5 on 2010-11-24
hello, my dad has a dell dimension 2400 and i can.t enable the desktop effects, and it comes with an intel graphics controller. i.m not exactly sure how to do anything with this, so if anyone can step-by-step me through it, i would appreciate it.

thanks in advance.

---

### Post by yankysunny on 2010-11-24
What type of desktop effects are you looking for? The basic one u can find in Appearance menu

---

### Post by igotsanevo4g on 2010-11-24
[http://ubuntuforums.org/showthread.php?t=1629678](http://ubuntuforums.org/showthread.php?t=1629678)

---

### Post by LADmaticCA on 2010-11-24
When I put Ubuntu on my auntie's Dell Dimension, I had trouble enabling effects as well. What I ended up doing was editing the xorg.conf file and changing the Driver to "intel." This was back in jaunty, but might still work.

Maverick does not use an xorg.conf file by default so you would have to generate one. Do this by rebooting and choosing the recovery console, drop to root shell and type:

```
Xorg -configure
```

It will create a file called xorg.conf.new in the /root location. This must be copied to the /etc/X11/ directory and renamed to xorg.conf. To do so type:

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

Now you must edit the xorg.conf file.

```
nano /etc/X11/xorg.conf
```

Find the Device section and change the Driver line to read:

```
Driver "intel"
```

Press Ctrl+O to save the changes. Then Ctrl+X to exit.

Then type *exit* and reboot. Hopefully it helps.

---

### Post by owners4life5 on 2010-11-25
thanks for the suggestions, none of them work though.

---

