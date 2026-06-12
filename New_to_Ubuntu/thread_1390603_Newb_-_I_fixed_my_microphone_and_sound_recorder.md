---
title: "Newb - I fixed my microphone and sound recorder"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by neophyte_of_linux on 2010-01-25
This is for reference for any other person who it may or may not help. I'm a very newby neophyte of ubuntu and computers.

I installed hardy heron on an old Powerspec PC desktop.

I wanted to experiment with creating my own audiobook by recording myself reading some literature. The idea was to make an out of print book available for vision impaired persons or others, maybe podcast or download if ever I learn those things.

I have a nice Sony stereo microphone. But when I would use sound recorder, nothing would happen but the program freezing. Same with Audacity. I couldn't tell even if my microphone was detected since it wouldn't capture.

I got it to work by fooling around with the settings on the volume control program. This baffled me at first because it shows about 4 "devices" available and I have no idea what it all meant. The default window showed my microphone slider as on (i.e. no red x), this "device" was 0: Sis SI7012 (Alsa mixer).

By trial and error I found some of the microphone sliders were set to "off" (red x) on devices that wasn't the selected choice.  I turned on the microphone for all of them.  Then I was able to record sound!  Sound Recorder and Audacity got signals and recorded (although volume is too faint even with sliders maxed).

The other devices were:
1: Realtek AIC655 rev 0 (OSS Mixer)
2: Playback: Alsa PCM on front : 0 (Sis SI 7012) via DMA (PulseAudio Mixer)
3: Capture: Monitor source of ALSA PCM on front: 0 (Sis SI 7012) via DMA (PulseAudio Mixer)
4: Capture: Alsa PCM on front : 0 (Sis SI 7012) via DMA (PulseAudio Mixer)

So basically I had to select each device, look at it and the tabs, and made sure the microphone was on and the slider up.

I would have thought if I wasn't using but the one device selected the settings on the others wouldn't have mattered because those devices "weren't on" in my mind.

Maybe this is all obvious.  If so enjoy a chuckle about my enlightenment!

---

