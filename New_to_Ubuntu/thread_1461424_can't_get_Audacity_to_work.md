---
title: "can't get Audacity to work"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by telltom on 2010-04-24
I'm a dual booter and Audacity works fine in windows, but i can't get it to work in Ubuntu.
any help appreciated.

---

### Post by indytim on 2010-04-24
1.  Do you have lame installed (required)?  Refer to [http://wiki.audacityteam.org/index.php?title=Lame_Installation#GNU.2FLinux.2FUnix_instructions]("http://wiki.audacityteam.org/index.php?title=Lame_Installation#GNU.2FLinux.2FUnix_instructions") for specifics.

2.  Also refer to the Audacity site for additional information at [http://audacity.sourceforge.net/]("http://audacity.sourceforge.net/")

-IndyTim

---

### Post by telltom on 2010-04-24
thanks for help. yes i have Lame installed. but still not working. I plug in mic and try to record but the line doesn't move and no recording. I read the help menu, but all my settings seem to be ok.

---

### Post by ajgreeny on 2010-04-24
Use ```
alsamixer
``` in terminal to ensure the mic is not set too low or even muted.  Also install **padevchooser** if you don't have it, and play around with **sound preferences** from a click on the volume icon and **pulseaudio volume control** from the sound and video menu.

I have audacity working well on my system now, but it took a bit of fiddling to do so, and trial and error in those two sound setting utilities.

---

### Post by telltom on 2010-04-24
i just tried a recording I extracted with sound juicer  and it works fine, but i can't get a mic to work. Also I tried recording with a different mic and same result, nothing.

---

### Post by ajgreeny on 2010-04-24
I agree that the sound settings in ubuntu are a bit confusing now with pulse, but I suspect that you either have the wrong settings in your pulseaudio volume control, or that the capture levels are set too low in some way.

Check on the **pulseaudio volume control - Input devices** tab that you have the settings as you want them, and that there is a movement on the level meter that shows there.  Just keep trying different settings and I'm sure you will eventually get it to work.

---

