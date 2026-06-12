---
title: "Getting 5.1 to work"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-07-18
Hey guys,

today, I bought a small 5.1 surround system and hooked it up to my 7.1 sound card (nVidia Corporation MCP61 High Definition Audio). It's the very first time in my life that I have my own 5.1 system, so far, I always used stereo. I'm on Ubuntu Jaunty 64 bit.

I think I connected all the cables and speakers correctly, and then I ran a DVD on VLC Media Player. The sound came in stereo at first, but from all speakers. When I switched the output to 5.1, though, I got the following error message:

> Audio output failed:
The audio device "surround51" is already in use.
Audio output failed:
VLC could not open the ALSA device "surround51" (Device or resource busy).

Did I fail to install some software? In my volume controls, I can activate all the necessary sliders, and when I slide them up/down, I can regulate the volume of each single speaker/subwoofer on its own. So everything is set up correctly.

Now how do I get the software to play along? Any ideas? Thanks, they're really appreciated! :-)

---

### Post by The Bright Side on 2009-07-18
I've been toying around with it a bit, but I can't get the 5.1 to run correctly. When I type

speaker-test -Dplug:surround51 -c6 -l1 -twav

in the terminal, the sound is played back correctly from the speakers/subwoofer, but in VLC, when using this test AVI

[http://www.tfm.ro/ac3/](http://www.tfm.ro/ac3/)

I don't get the correct sound. The center is fine, but all variations of left and right come from both front, back and LFE (left and right respectively). This happens in both ALSA and Pulse.

---

### Post by The Bright Side on 2009-07-20
I got it to work. For whoever runs into the same problem: for me, it was just a matter of endlessly fiddling around with the settings. Here's the setup in VLC that now works for me (pretty straightforward, actually):

- First, select "All" in "Show Settings" in the options menu
- Under "Audio", I have "High Quality Audio Resampling" enabled (it is by default, I think)
- "Use S/PDIF when available" is disabled
- "Peak Protection" disabled, too

- The selected Audio output module is "ALSA audio output"
- In the sub-options of "Output modules", I selected "HDA Nvidia: ALC888 Analog (hw:0,0)" as my ALSA Device Name
- Under "OSS", I enabled "Try to work around buggy..."

Now I can select "5.1" from the Audio Device menu when playing back a DVD, and it works.
Thanks again!

---

