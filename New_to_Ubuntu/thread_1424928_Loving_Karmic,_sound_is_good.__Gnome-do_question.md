---
title: "Loving Karmic, sound is good.  Gnome-do question"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by SquirmyDude on 2010-03-08
Hi, I just installed running Karmic 64 bit.  I have used Ubuntu before and loved it but quit using it on this AMD dual core box because I couldn't get the sound figured out.  Now the sound works great, thanks for the great work.  You can tell how good a distro is by the triviality of the problems, I suppose. :)  Anyway, here goes.  I can't seem to get gnome-do to startup on boot.  I've added /usr/bin/gnome-do to the startup aps, but it doesn't seem to execute.

---

### Post by Method X on 2010-03-08
> **SquirmyDude said:**
> Hi, I just installed running Karmic 64 bit.  I have used Ubuntu before and loved it but quit using it on this AMD dual core box because I couldn't get the sound figured out.  Now the sound works great, thanks for the great work.  You can tell how good a distro is by the triviality of the problems, I suppose. :)  Anyway, here goes.  I can't seem to get gnome-do to startup on boot.  I've added /usr/bin/gnome-do to the startup aps, but it doesn't seem to execute.

I had same problem on my ubuntu x64.
But now i'm on x86, and don't need gnome-do. I use kupfer. Same as gnome-do, written on pyton.

---

### Post by SquirmyDude on 2010-03-08
Thanks, I looked at kupfer and gnome-launch-box.  They both looked like they work and will launch on startup, but I like the "docky" mode of gnome-do.  For now I just added a launcher on the panel.  I'm just glad I have great sound, and can use Skype again.:p

---

### Post by MichealH on 2010-03-08
> **SquirmyDude said:**
> Hi, I just installed running Karmic 64 bit.  I have used Ubuntu before and loved it but quit using it on this AMD dual core box because I couldn't get the sound figured out.  Now the sound works great, thanks for the great work.  You can tell how good a distro is by the triviality of the problems, I suppose. :)  Anyway, here goes.  I can't seem to get gnome-do to startup on boot.  I've added /usr/bin/gnome-do to the startup aps, but it doesn't seem to execute.

Karmics New splash stops some apps like conky from runing at startup- Gnome-Do is annother one of those programs. Make a new sh file called lets say gnome-do_strtup.sh and then put this in

```
#!/bin/bash
sleep 20 && /usr/bin/gnome-do;
```

Oh and add that file to your startup apps!

---

### Post by Method X on 2010-03-08
> **MichealH said:**
> Karmics New splash stops some apps like conky from runing at startup- Gnome-Do is annother one of those programs. Make a new sh file called lets say gnome-do_strtup.sh and then put this in

```
#!/bin/bash
sleep 20 && /usr/bin/gnome-do;
```

Oh and add that file to your startup apps!

oh thx for that. now i now why it doesn't work in gnome and work in xfce ;)

---

### Post by SquirmyDude on 2010-03-08
Hi, Thanks, but I couldn't get that script to work either.  I've decided to use cairo-dock, instead.  That seems to work on startup with the option cairo-dock -c.  Fortunately, Linux has so many great options.

---

### Post by Method X on 2010-03-09
> **SquirmyDude said:**
> Hi, Thanks, but I couldn't get that script to work either.  I've decided to use cairo-dock, instead.  That seems to work on startup with the option cairo-dock -c.  Fortunately, Linux has so many great options.

didn't you forget to apply this command to your script:

```
sudo chmod +x your-script
```

;)

---

