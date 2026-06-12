---
title: "How to record online sound"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by timbo59 on 2010-11-28
Hi again,
             I needed to record some online sounds for some effects I'm looking to add to a home video. Via XP I'd just have to click on the volume tab in the tray and switch recording to 'what you hear' and any sound piping through the PC I could record via Audacity. Via Ubuntu, I can't seem to figure out how to accompish the same thing. I've clicked on every variation on Sound preferences/Input, but nothing seems to work - the graph on Audacity stays flat as a tack.

Can anyone clue me in on what I'm missing here?

---

### Post by rmockler on 2010-11-28
Go to Applications-->Sound & Video and see if Sound Recorder appears there.
If not, then go to Synaptic Package Manager and search for gnome-sound-recorder.
Install it, and it should then appear in Sound & Video.

---

### Post by timbo59 on 2010-11-29
Actually, I already tried that as an alternative to Audacity, just in case it was a software issue. I clicked up Youtube, recorded sound from the first thing I saw, and the file generated came up a dud - not a peep on it. Something, somewhere, needs to be enabled, but I'm so unfamiliar with Ubuntu that I don't know where to look. 

Anyone have any ideas?

---

### Post by timbo59 on 2010-11-29
Solved it - I think! I managed to get recordings in both Audacity and Sound recorder by switching to microphone 1 - that's the only thing that would register while recording - the other four choices registered nothing in the recordings. Only problem is that, even though I've set the input volume right up, the recordings are at a very low volume. I can boost it later in a program like Audacity, but it would be better to have it recording at the right volume to minimize distortion in the amplitude boosting. Is there a master input volume control elsewhere that needs to bumped up?

---

### Post by rmockler on 2010-11-29
Go to System--> Preferences--> Sound
Click on Sound, then click on the tab for Input.
That should take care of your problem.

---

### Post by timbo59 on 2010-12-12
Just to return to this, I recently tried again, but the volume was just atrocious. I had to bump it up by 23db in Audacity, which got it to where it should be, but amplified background static to ridiculous proportions, as would be expected. Trying to remove the unwanted sound affected the sound file too much. 

I had already gone the route of checking System/preferences/sound - the input volume is set to max. 

I just can't figure this. Never had such a problem before with my old computer on XP - all I had to do was hit 'what you hear' and everything worked swimmingly.

---

### Post by Vaphell on 2010-12-12
vlc is able to dump streamed data to a file, also you can use ffmpeg to rip audio track directly from the source - completed flash movies from youtube or whatever can be found in the cache of your browser.

---

### Post by timbo59 on 2010-12-12
Thanks....I'll give that side of it a whirl. 

Any ideas on why the input volume is so low? What's strange is that the output side of it is fine - if I play something off youtube the volume is loud and clear - yet if record the same bit via Audacity the input levels shown are very low, even with the input volume level set at max.

---

### Post by timbo59 on 2010-12-12
Hi again,
             Okay, I've been playing around with VLC but can't quite figure what you mean by dumping to a file. How exactly do I make VLC do that?

---

### Post by erilidon on 2010-12-12
make sure the input mic is turned up. try "alsamixer" in the terminal then press "F4" for all the capture devices.

---

### Post by timbo59 on 2010-12-13
Mike is set to max. already. It's really strange - I play something off Youtube for test purposes, and eve though I can see the mike level set to 100% the input level indicator never goes past the second bar - even if I pick out something really 'loud' to test it on. 

I just can't figure this. 

Can anyone get back to me on how to use VLC to put streamed data on a file? Maybe I can get around the volume issue that way.

Thanks.........Tim

---

### Post by StrobeWylan on 2011-01-24
I'm trying to accomplish this same thing but can't seem to find a way. I read on the audacity site that the version available via Ubuntu software Center is Audacity 1.3.12 (Beta) and it's using an (experimental) v19 version of PortAudio which hasn't got PortMixer support. It says we need to have PortAudio v18 in order to set it to wave out or whatever we need so as to record streaming audio. I read a post here that had a complicated (for me) way to use terminal to record streaming audio and it worked for me but is way to complicated to do in a pinch when I need to start recording quickly. 

I have not been able to find an older stable version of Audacity such as 1.2 where v18 PortAudio is used.

Any body have some time to help this newbee.

---

