---
title: "system sound issue"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Matt26 on 2009-01-06
i get this message when i try to open amarok or play music files sometimes:

xine was unable to initialize any audio drivers.

i then have to restart my computer in order to get amarok to play music files again.

i have tried suggestions about changing the sound options under System/Preferences/Sound but with no success.

i continue to experience this issue and it seems to be affecting all sound playback on my system as well- i tried using another media player and i get no sound.. when i go into System/Preferences/Sound and click on the Test button next to any of the sound options (all set to auto-detect) i get this error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused

i am using amarok v1.4.1.0 on ubuntu 8.10.

any help would be greatly appreciated.

thanks.

---

### Post by gettinoriginal on 2009-01-15
These two set mine up perfectly:  If the first one doesn't fix it, then do the second, only takes about 15 minutes.  :p

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=789578&highlight=usb+mic](http://ubuntuforums.org/showthread.php?t=789578&highlight=usb+mic)

---

