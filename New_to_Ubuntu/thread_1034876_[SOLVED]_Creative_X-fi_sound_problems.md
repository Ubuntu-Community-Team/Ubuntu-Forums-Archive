---
title: "[SOLVED] Creative X-fi sound problems"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by loseby on 2009-01-09
When I double click on the sound icon in the panel the Volume Control for the Creative X-fi (alsa mixer ) opens., I have gone to the switches and ticked digit-io ( this should be the digital sound as my speakers are digital ) but still no sound.


I go to System/preferences/sound and make sure Creative x-fi ALSA wave in/wave out is selected but when I test I get the following message

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

I have a hardware HTML that shows

id:	
multimedia
description: 	Multimedia audio controller
product: 	SB X-Fi
vendor: 	Creative Labs
physical id: 	
2
bus info: 	
pci@0000:05:02.0
version: 	00
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi bus_master cap_list
configuration:	
latency	=	32
maxlatency	=	5
mingnt	=	4


So I am confused ? any ideas on how to get sound ?

edit: just turned it back on and it screamed ( had the volume way up ) and then a foreign voice started talking . I thinks its olca sreen magnifer and talker. Anyway played around and changed all my setting to pulseaudio instead of x-fi alsa and now have sound and can play music. 

So now have sound and was wondering if anyone knows how I can increase my bass settings ?

---

