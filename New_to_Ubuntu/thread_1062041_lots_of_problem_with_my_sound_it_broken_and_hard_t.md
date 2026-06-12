---
title: "lots of problem with my sound it broken and hard to describe"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by viswanathan on 2009-02-06
guys i reinstalled my ubuntu (second time i guess ) and bang ! sound is horrible its completely broken its like  a DJ in my system !!!!!!! well as usual went with wiki troubleshooting guide bu of no use . i have no idea whats wrong . last time a guy named nyaa helped me in #ubuntu irc , what he did was he added a line to some file i have no clue which file was it guys. here is the wiki and the paste bin of general things 

[HTML]https://help.ubuntu.com/community/SoundTroubleshooting[/HTML]

[HTML]http://paste.ubuntu.com/114860/[/HTML]

---

### Post by jbrown96 on 2009-02-06
Are you using Pulseaudio? It seems to be a frequent problem with that audio chipset, although I have the same one with no problems. go to System--->Preferences--->Sound and change all of the devices to ALSA. 

Then open a terminal and ```
alsamixer
``` You should see several channels. Unmute all the channels and turn them up all the way, except master put it around 80. Go back to the sound preferences. and choose to test audio playback. You should now hear a tone. Go back to alsamixer, with the tone still playing, and mute all of the channels that you don't need. you usually need master, pcm, and front, but may need others (i.e. microphone if you use one). Basically, we want to mute all but the necessary channels because they can cause feedback.

---

### Post by viswanathan on 2009-02-06
> **jbrown96 said:**
> Are you using Pulseaudio? It seems to be a frequent problem with that audio chipset, although I have the same one with no problems. go to System--->Preferences--->Sound and change all of the devices to ALSA. 

Then open a terminal and ```
alsamixer
``` You should see several channels. Unmute all the channels and turn them up all the way, except master put it around 80. Go back to the sound preferences. and choose to test audio playback. You should now hear a tone. Go back to alsamixer, with the tone still playing, and mute all of the channels that you don't need. you usually need master, pcm, and front, but may need others (i.e. microphone if you use one). Basically, we want to mute all but the necessary channels because they can cause feedback.

just changed to pulse-audio after this thread [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by viswanathan on 2009-02-06
did as you said still of no use

---

