---
title: "Two problems -- microphone and hibernation"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by cls- on 2010-03-30
I installed Ubuntu 9.10 on my HP Pavilion Entertainment PC yesterday. However, I have encountered two problems.

1) The microphone portion of my Logitech microphone/headset combination doesn't seem to work. I've tried using the Sound Recorder, I've fiddled with the sound preferences, but it still doesn't work. The headset isn't the problem because I'm able to listen to music and other audio fine.
2) I put my computer on hibernate before I left my home. When I came back, I tried to boot it back up, but all I got was a black screen with what appeared to be the Terminal in the top left. I tried restarting, but I encountered the same error. I've reinstalled the operating system from the disc.

So basically, I'm stuck.

---

### Post by lidex on 2010-03-30
As for the microphone:
> To record sound one must enable the relevant capture controls. Since different cards can have very different mixers, which ones are relevant depends a lot on the card. It is best to explore the various channels and controls using alsamixer and pressing F5 to see the full set of capture controls.

Despite the wide variation in mixers, there are some common types and names of controls:

    * If input channels like Mic or Line In also have a playback control and a volume control that allows routing their input to the output, that means that their input can be routed to the output, which allows monitoring what is being recorded.
    * If output channels like PCM or Synth also have a capture control that allows routing their output into the input, which enables recording what is being played.
    * If there is a Capture channel usually that must be set in capture mode enabled for any recording to happen. If other channels, for example Line In can be set in capture mode that is to allow to control which input channels are mixed into the input channel.
    * If there is a Mix channel that can be set in capture mode that must be set to allow recording of sounds being played. Usually if this channel exists there are no capture controls on individual output channels, and the complete mix of all output channels is recorded.

Probably each card needs a bit of experimenting to figure out the roles of the various channels and their controls. These can be rather unobvious.

Once the capture mode has been selected, one can use some kind of recording application, for example arecord, selecting the right recording device. This can be usually a direct specification like hw:0,0 (for the analog recording device) or a virtual device name defined in an asound.conf file like dsp0; in the latter case it must be defined as a dsnoop plugin or an asym plugin.

With most cheap microphones out there one usually has to enable the (usually low quality) internal input amplifier by unmuting a suitable channel, usually called Mic Boost.

In most recent low cost chipset recording can only be done at a single fixed rate, usually 48000Hz, or at one of two fixed ones, usually 48000Hz and 44100Hz. If you want a different frequency you can resample after recording or use the plug: prefix on the name of the chosen recording device (or plughw: if it is a hw: device). For example:

arecord -D plughw:0,0 -f S16_LE -c 2 -r 22050 record.wav

From this page:
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html]("http://www.sabi.co.uk/Notes/linuxSoundALSA.html")

Anyway, open a terminal (applications>accessories>terminal) and enter this command:
```
alsamixer
```
Press F6 and make sure the proper soundcard is selected.
Pess F4 to view capture devices. Use the arrow keys to navigate elements and change values.

---

### Post by J V on 2010-03-30
Hibernation is still experimental in linux, and will be for a while... Thats why Lucid is supposed to boot up in 10 seconds :)

Works with some HW doesn't with others.

Did you try pressing ctrl-alt-F1, ctrl-alt-F7? if that doesn't get you back in, you will need to log in there and type in "gnome-session" to start up the GUI and shut down normally...

---

### Post by lidex on 2010-03-30
Suspend might work better? You can change some options in "System>Preferences>Power Management"

---

