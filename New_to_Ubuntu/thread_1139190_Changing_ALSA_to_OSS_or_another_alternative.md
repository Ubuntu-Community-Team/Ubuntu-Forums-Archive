---
title: "Changing ALSA to OSS or another alternative"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by comrademauri on 2009-04-26
Hi all, I've been searching all around the internet and these forums for help but i haven't seen anything that can help me.

I've been using ubuntu for a while and i never was able to get the microphone to work. I recently upgraded to 9.04 and still no luck "out of the box" since my sound card **(Intel HDA [ICH8 Family]**) seems to not be supported by ALSA but im pretty sure its supported by OSS. 

So my question is, how do i go about changing the setup from ALSA to OSS or some other alternative? help would be appreciated and i'd give out any details that i can 

Dell Insipiron 1318 laptop
ubuntu 9.04
(Intel HDA [ICH8 Family]) Sound Card
webcam/microphone work on vista partition so its not a hardware problem

---

### Post by Mark Phelps on 2009-04-27
According to 4Front, your chip is supported.

Go to the link below, and you will find links to download the packages and a forum with support:

[http://www.opensound.com/oss.html]("http://www.opensound.com/oss.html")

---

### Post by comrademauri on 2009-04-27
Thanks, it installed fine. Speakers and headphones work but still no microphone :(

I opened up System>Preferances>Sound and switched everything to OSS4 and i checked every box in the preferances window of the volume control and raised the volume up all the way but still no luck. 
When i open up Sound Recorder the only input device is "rec1-mux" and when i click record, this error message pops up:

> Could not capture using the 'CD Quality, Lossy' audio profile. Please verify its settings.
You may be missing the necessary plug-ins.

and also when i open up the volume control and go to the recording tab, theres always an X over all the input devices. i click them so they are unmuted but when i open it up again they have the X over the mic again. i had that same problem with ALSA

this isnt really a high priotity problem for me since i only wanted the mic for skype but i ended up installing it on my vista partition anyways so I've kind of given up with the ubuntu mic. 
thanks for the help mark, i'll ask around on the 4front forums and if i find a solution i'll post it here for future referance.

---

### Post by Didius Falco on 2009-04-27
> **comrademauri said:**
> Thanks, it installed fine. Speakers and headphones work but still no microphone :(

I opened up System>Preferances>Sound and switched everything to OSS4 and i checked every box in the preferances window of the volume control and raised the volume up all the way but still no luck. 
When i open up Sound Recorder the only input device is "rec1-mux" and when i click record, this error message pops up:



and also when i open up the volume control and go to the recording tab, theres always an X over all the input devices. i click them so they are unmuted but when i open it up again they have the X over the mic again. i had that same problem with ALSA

this isnt really a high priotity problem for me since i only wanted the mic for skype but i ended up installing it on my vista partition anyways so I've kind of given up with the ubuntu mic. 
thanks for the help mark, i'll ask around on the 4front forums and if i find a solution i'll post it here for future referance.

Go through this HOWTO. It's a great resource to bookmark.

[http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working)

I hope it helps...

---

