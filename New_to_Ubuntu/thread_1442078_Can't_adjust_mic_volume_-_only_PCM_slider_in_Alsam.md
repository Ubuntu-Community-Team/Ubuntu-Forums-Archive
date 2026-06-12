---
title: "Can't adjust mic volume - only PCM slider in Alsamixer, 9.10"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by MorrisseyJ on 2010-03-29
I am having some sound problems on Karmic.

I can't seem to increase the volume of my microphone. The microphone works but its a little soft - people that i am speaking to on skype complain and after using the sound recorder i can see why. 

I have tried turning up the slider under 'input volume' in 'sound preferences' but that does nothing.

I have looked in alsamixer but i find that the only slider i have is PCM. I can't seem to move any of the other sliders which are all set at '00'. I am guessing that this is my problem regarding being unable to change the sound on my mic. 

After looking on the forums i see that there have been a number of problems with Karmic and sound. The closest one that i could find to this problem - assuming that the problem is the lack of sliders in alsamixer - is this one [http://ubuntuforums.org/showthread.php?t=569035](http://ubuntuforums.org/showthread.php?t=569035) , but it remains unanswered.

What i don't understand, in my case, is how my microphone is working at all if the sliders are at 00. 

I saw somewhere else that someone mentioned removing pulseaudio as that imposes some automatic setting on alsamixer. I was thinking of doing this but got scared off by having read other stuff that pulse audio is needed for skype (i think). 

Any advice on either how to fix alsamixer, or if thats not the problem, how to adjust my mic volume would be greatly appreciated.

---

### Post by lidex on 2010-03-29
> Skype: The latest release of Skype has native PulseAudio support, and does not require special configuration. If you are using an older version, continue reading. Open Skype's Options, then go to Sound Devices. You need to set "Sound Out" and "Ringing" to the "pulse" device, and set "Sound In" to the hardware definition of your microphone. For example, my laptop's microphone is defined as "plughw:I82801DBICH4,0".
Any help?

---

### Post by MorrisseyJ on 2010-03-30
Not really. I have the latest version of skype downloaded and it seems to configure with pulseaudio

I still seem unable to change the volume of my microphone. 

I am also totally unsure why i only have one PCM slider in alsamixer - is this something that pulseaudio has done and if so does anyone else have this issue?

---

### Post by MorrisseyJ on 2010-03-30
I have just downloaded the Gnome-Alsamixer. On the graphic interface i can adjust the volume controls - something that could not do in the terminal setup of Alsamixer. 

I have also embarisgnly discovered that what i referred to as 00 in the original post about alsamixer actually appear to be infinity signs. So it seems that i have the volume set to infinity on all the setting but PCM. PCM being the only one that i can fiddle with.

Back to the GUI for alsamixer, i see that the volume control is muted for my microphone. Thinking that my issue lay here i un-muted it and adjusted the slider but it made no difference to the volume of my mic. I see now that i can actually use both sound recorder and do a working skype test with the volume remaining muted in the Gnome-alsamixer

It seems that my alsamixer has been entirely over ridden by something else. Anyone have any ideas about the relationship between pulseaudio and alsamixer, and what skype might have done to these?

---

### Post by lidex on 2010-03-30
Sorry for the dump but I have to go. There seem to be a number of things. Look through these links:
[http://www.google.com/search?q=skype+microphone&sitesearch=ubuntuforums.org]("http://www.google.com/search?q=skype+microphone&sitesearch=ubuntuforums.org")

---

### Post by MorrisseyJ on 2010-03-31
Thanks for this.

After looking around i downloaded the Pulse Audio Volume control. For anyone else who stumbles across this thread its available in the repository. 

In the volume control i see that my microphone volume i maxed out. Notably though the volume does go down and mute when i fiddle with these settings. So it seems like the mic is just a little soft at the moment, but at least i know how to control it. 

I am still not sure if i can make the microphone any louder, i am fairly sure it was louder under windows. That said i am going to mark this thread as solved as i have now worked out how to get control of the volume on my mic and the thread is beginning to wander. 

With this in mind if anyone finds this thread and knows what the relationship is between alsamixer and pulseaudio i would appreciate the information. When i have some time i'll try installing each one and using them separately to see if there is any difference. 

I'll post back if i find anything, or if i break anything...

---

