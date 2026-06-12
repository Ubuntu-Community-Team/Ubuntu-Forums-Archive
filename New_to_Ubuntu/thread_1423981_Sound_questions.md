---
title: "Sound questions"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by recycledhippy on 2010-03-07
I've been using Ubuntu for some time now and still am a little lost at times. I have been trying do do some music stuff and have been having some problems with sound. What is Pulse audio? What is alsa? what is JACK? Is there a common set-up that works with most programs? any help with this would be great. thanks!

---

### Post by recycledhippy on 2010-03-07
oh yeah, Is there a way to tell witch one you have installed or currently running? I think I my have made a mess with my audio.

---

### Post by recycledhippy on 2010-03-07
please, someone help me out.

---

### Post by recycledhippy on 2010-03-20
any help?

---

### Post by 801TomAK on 2010-03-20
here do this     Static sound should be only in apps and games not for ubuntu sounds. Now the current audio driver "pulse audio" caused static in some apps and switching to ALSA fixed that. You can get it by running,  	Code:
 	sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get install alsa-base linux-sound-base alsa-utils
sudo apt-get install gnome-alsamixer

---

### Post by 801TomAK on 2010-03-20
forget about what it says lol just run the sudo apt-get stuff and you shouldnt have any sound issues cause Alsa works for about every thing

---

