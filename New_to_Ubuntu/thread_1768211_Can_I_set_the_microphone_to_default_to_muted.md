---
title: "Can I set the microphone to default to muted?"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by skitter on 2011-05-26
I'm using Natty (11.04) on a thinkpad t420.  I see that I can go to the sound preferences application and mute the microphone on the input tab.  The mute check box is unchecked when I reboot though. Is there a way to keep the mic muted after a reboot?

---

### Post by ajgreeny on 2011-05-26
ALSAMIXER
Run ```
alsamixer
``` in terminal and check that the levels are set where you want them.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

I assume alsamixer is still available for natty.

---

### Post by skitter on 2011-05-26
Thanks! Now the mic is staying muted when I reboot.

---

### Post by krtica on 2011-10-17
Hm... Strange. I have exactly same problem on my Thinkpad T520, but I don't have "mute" option under microphone level... :(
Lots of issues with muting unmuting microphone on this laptop under 11.04, and I can't go back to 10.04 LTS :( because it doesn't support "sendibridge".
Terible, terible. :D

---

