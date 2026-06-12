---
title: "Sound not working after update."
date: 2010-03-03
forum: New to Ubuntu
---

### Post by thom# on 2010-03-03
An update was run on my computer and now the sound has stopped working. I have checked the settings in ALSA mixer and they are correct.

I have followed the instructions from [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) the sticky and my settings seem to be correct.

I think that something in the update must have caused the sound to stop working.

When I boot from the Ubuntu live CD the sound is working again. There seems to be no hardware fault.

Could you please advise on steps that I should take to fix this problem? I am unsure what was updated, or how to locate the list.

---

### Post by lyall on 2010-03-03
also check System > Preferences > Sound

check and see what the slide shows
and if it is muted

good luck and have fun learning

---

### Post by thom# on 2010-03-03
Thank you, I have checked the sound properties again, though nothing is muted. 

The packages that I updated were;

cups (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4
cups-bsd (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4
cups-client (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4
cups-common (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4
libcups2 (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4
libcupscgi1 (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4
libcupsdriver1 (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4
libcupsimage2 (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4
libcupsmime1 (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4
libcupsppdc1 (1.4.1-5ubuntu2.2) to 1.4.1-5ubuntu2.4

I will try to remove these to see if that removes the problem.

---

### Post by buddyd16 on 2010-03-03
thom#:
open a terminal (applications -> accesories -> terminal) and type
```
alsamixer
``` take a screenshot and post it here.

---

### Post by smmalmansoori on 2010-03-04
Right click on the sound icon > Sound Preferences > Choose the Output tab > Make sure you have the right output device selected, as that might have changed after the update?

---

