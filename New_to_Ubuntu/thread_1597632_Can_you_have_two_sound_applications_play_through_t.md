---
title: "Can you have two sound applications play through two sets of speakers?"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by mbyrd11 on 2010-10-15
So pretty much what I am wanting to do is to have totem playing through my stereo. and at the same time have Youtube videos playing through my headset without the totem.

Is there anything that will make this possible?

---

### Post by marshmallow1304 on 2010-10-17
This should be possible if you have multiple output devices (i.e. multiple sound cards or a sound card with multiple outputs).

Unfortunately, I don't have such a setup, so I don't know exactly how to do it.  Hypothetically, you would use the pavucontrol utility to direct output and possibly the paprefs utility to add a virtual device for simultaneous output.

If you don't know about the sound card(s), post the output of
```
aplay -l
```

---

### Post by mbyrd11 on 2010-10-17
> **marshmallow1304 said:**
> This should be possible if you have multiple output devices (i.e. multiple sound cards or a sound card with multiple outputs).

Unfortunately, I don't have such a setup, so I don't know exactly how to do it.  Hypothetically, you would use the pavucontrol utility to direct output and possibly the paprefs utility to add a virtual device for simultaneous output.

If you don't know about the sound card(s), post the output of
```
aplay -l
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Thats what I've got. do you think that i would be able to do this without buying a sound card?

---

### Post by marshmallow1304 on 2010-10-17
It looks to me like it should be possible, but I'm no expert on sound cards.  I'd start by installing pavucontrol and seeing what options you have in the Output Devices section.

---

### Post by sandyd on 2010-10-17
> **mbyrd11 said:**
> ```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Thats what I've got. do you think that i would be able to do this without buying a sound card?
its possible.

install pavucontrol.
when the music is both playing, open pavucontrol.

you can then choose which device you want to output it out of.

see screenshot

---

### Post by mbyrd11 on 2010-10-17
So are you right clicking to get that option box?
Because when i do that all I get is an option to terminate playback not an option to pick between output devices.

and i downloaded a Pulse Audio Volume Control from the repos is it the same one that you are using?

---

### Post by sandyd on 2010-10-17
> **mbyrd11 said:**
> So are you right clicking to get that option box?
Because when i do that all I get is an option to terminate playback not an option to pick between output devices.

and i downloaded a Pulse Audio Volume Control from the repos is it the same one that you are using?
its called pavucontrol.
mine may differ a bit. and its left click, not right click.

while your playing music, it should list the sound device that the music is playing out of beside the application (in the pavucontrol window)

---

### Post by mbyrd11 on 2010-10-17
I think that the problem is is that I only have my Internal Audio Analog Stereo as an output device. 
I don't have an actual soundcard, only the on-board audio of my motherboard.

and also im not getting anything with a left mouse click.
And it is listing the sound device as playback stream.

---

