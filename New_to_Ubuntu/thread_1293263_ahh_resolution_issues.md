---
title: "ahh resolution issues?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by zomg on 2009-10-16
so, i'm an ubuntu user as of 5 minutes ago. having the resolution probs that seem to be quite common. have tried follow some of the steps in the forums but i just can't seem to get it to work...
can someone give me some simple instructions pleeeease?!

---

### Post by nmccrina on 2009-10-16
This is pretty basic, but have you tried using System->Preferences->Display? There's a resolution chooser in there. If that doesn't work, I would think that you'll probably have to edit /etc/X11/xorg.conf, but I don't know much about that. You could try googling it to see what you could change in there.

BTW, nice screenname!

---

### Post by ibuclaw on 2009-10-17
What type of graphics card and monitor do you have?

Resolution issues usually happen because the monitor doesn't have an EDID built into it to give to the OS, and Ubuntu - by default - uses low frequency settings so older monitors aren't damaged.

Knowing the graphics card and monitor details means that:
[LIST=1]
[*]We can ensure that you are using the correct driver for the Card.
[*]We can ensure that when you tweak the xorg.conf file, you are using the appropriate Horizontal and Vertical Frequency settings for your monitor to operate at it's designed values.
[/LIST]

Regards
Iain

---

### Post by Big_Croc7 on 2009-10-17
STOP!

Read this:
[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

---

