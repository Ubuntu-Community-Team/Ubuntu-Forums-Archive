---
title: "Microphone doesn't work"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by birdwin on 2009-08-09
Hello all.

I can't seem to get Sound Recorder working. 'lspci -v | grep Audio -A 6' yields:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 0220
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dfdfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

and 'aplay -l' yields:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

After I unmute both Capture lines in the Recording tab of Volume Control and hit OK, when I go back into Volume Control they're muted again. I've got a headphone and mic jack on both the front and back of the PC. Thanks for the help.

---

