---
title: "sound issues 9.10"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by now_here on 2010-03-04
so i just built my first box about 6 weeks ago and decided to finally take the plunge and try ubuntu for it. 

sound had been totally fine without any configuration on my part up until a few days ago, when i tried to play some music from rhythmbox, and there was no sound. i checked the various volume sliders, played around with em, checked the sound connection to the monitor (where the speakers are), everything checked out, still no sound. the tracks were playing, but at about double normal speed (according to the seek bar). (edit) just realized youtube videos play doubletime as well (with no sound)

no sound from any other programs i tried (firefox, vlc and movie player), although i did get about half a second of sound from a yutube video before it cut out again. 

tried searching the forums, but only turned up stuff that didn't apply to me or was somewhat over my head. 

any help would be greatly appreciated.

---

### Post by smmalmansoori on 2010-03-04
Check out the Output tab in Sound Preferences, the default output device might have changed after an update?

---

### Post by lidex on 2010-03-04
There could be a number of things going on. You really don't provide enough info to make a diagnosis. Your first step is to check all the basic things and a checklist would be much more efficient. Work through this page first:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

If you don't understand something ask specific questions here. In the meantime, run these commands in a terminal ("applications>accessories>terminal"). Copy-and-paste the commands and press enter. If it prompts for a password, enter your user password, which will not display for security reasons.

For this one please post the terminal output text to this thread:
```
uname -a
```

Just run these, one line at a time and reboot:
```
sudo apt-get remove sl-modem-daemon
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

---

### Post by now_here on 2010-03-04
seems like it was the sound output. thanks guys

---

