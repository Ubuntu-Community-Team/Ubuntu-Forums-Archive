---
title: "Mic Boost issues"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by mlaw on 2009-09-08
Hello all!

For the past week or so I've been fiddling with my sound system in an attempt to get my microphone working.  A brief history:

When I installed Ubuntu 9.04, one of the first things I did was install Wine so that I could play WoW and run Ventrilo.  Happily, I was able to do both quite well, with the exception of being able to speak to anyone over Ventrilo (I could hear just fine).  

Because Ventrilo didn't work, I downloaded Skype to see if I could communicate over that.  Other programs I've attempted, but failed, to record on include Audacity and WoW.

Most of the fora I read suggest increasing the mic boost.  I've read a lot of them.  

Let me be very clear: there is no mic boost option.  At all.  In any form.  Not under preferences, not under alsamixer.  No where.  The *amixer controls | grep 'Mic Boost' *command appears to do nothing (there is no output associated with it).

I suspect this is related in some way to my sound card and a lack of supporting drivers but I don't know how to check that.  Perhaps it's related to PulseAudio.  I AM able to hear myself in the System->Preferences->Sound menu under the Devices tab.  I AM able to record myself using the Sound Recorder.

*aplay -l* returns:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [Microsoft LifeChat LX-3000 ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The Microsoft LifeChat LX-3000 is my USB headset.  I intend to use this device for communication.

I'd love any help anyone is able to offer!  These forums have been extremely instructive but do not seem to have a solution for this problem.  If the solution is "There is no solution", that'd be welcome news too!

EDIT:
Output of *amixer controls*:
numid=33,iface=MIXER,name='Master Playback Switch'
numid=32,iface=MIXER,name='Master Playback Volume'
numid=34,iface=MIXER,name='PCM Playback Volume'
numid=12,iface=MIXER,name='Front Playback Switch'
numid=11,iface=MIXER,name='Front Playback Volume'
numid=14,iface=MIXER,name='Surround Playback Switch'
numid=13,iface=MIXER,name='Surround Playback Volume'
numid=16,iface=MIXER,name='Center Playback Switch'
numid=15,iface=MIXER,name='Center Playback Volume'
numid=18,iface=MIXER,name='LFE Playback Switch'
numid=17,iface=MIXER,name='LFE Playback Volume'
numid=22,iface=MIXER,name='Line In as Output Switch'
numid=6,iface=MIXER,name='Capture Switch'
numid=8,iface=MIXER,name='Capture Switch',index=1
numid=10,iface=MIXER,name='Capture Switch',index=2
numid=5,iface=MIXER,name='Capture Volume'
numid=7,iface=MIXER,name='Capture Volume',index=1
numid=9,iface=MIXER,name='Capture Volume',index=2
numid=4,iface=MIXER,name='Analog Loopback'
numid=31,iface=MIXER,name='IEC958 Default PCM Playback Switch'
numid=27,iface=MIXER,name='IEC958 Playback Con Mask'
numid=28,iface=MIXER,name='IEC958 Playback Pro Mask'
numid=29,iface=MIXER,name='IEC958 Playback Default'
numid=26,iface=MIXER,name='IEC958 Playback Source'
numid=30,iface=MIXER,name='IEC958 Playback Switch'
numid=1,iface=MIXER,name='Input Source'
numid=2,iface=MIXER,name='Input Source',index=1
numid=3,iface=MIXER,name='Input Source',index=2
numid=23,iface=MIXER,name='Mux Capture Volume'
numid=24,iface=MIXER,name='Mux Capture Volume',index=1
numid=25,iface=MIXER,name='Mux Capture Volume',index=2
numid=21,iface=MIXER,name='Side Playback Switch'
numid=20,iface=MIXER,name='Side Playback Volume'
numid=19,iface=MIXER,name='Swap Center/LFE Playback Switch'

---

### Post by mlaw on 2009-09-09
bump

---

### Post by mlaw on 2009-09-11
Bump

---

### Post by RabbitWho on 2009-09-11
What's mic boost? 

This is probably the first thing you tried, but i didn't see it on your list, and it was the reason my mic wouldn't work for a while. 
"capture" is muted by default, so click on the speaker icon on the top taskbar, then the recording tab, then un mute the capture bars and move the slider up... 
Then click preferences and make sure the capture boxes are ticked. 

Sorry if you tried that already, maybe it will help someone else who stumbles across the thread.

---

### Post by sml on 2010-07-25
what is the answer here?

do we have mic boost or not?

---

