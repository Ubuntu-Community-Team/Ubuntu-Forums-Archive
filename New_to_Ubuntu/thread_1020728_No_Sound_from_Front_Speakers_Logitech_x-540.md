---
title: "No Sound from Front Speakers Logitech x-540"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by cnsinistral on 2008-12-24
Hello,

I've been using Ubuntu 8.04 for a few months and it's been great.  But I recently ran into a snag while trying to set up some logitech 5.1 x-540 speakers.  

The subwoofer, center, and two rear speakers work, but the two front speakers do not.

I cranked everything in alsamixer to the max setting to no avail (I should note that the tab reads "Realtek ALC888").

Here is what I get when I type **aplay -l**

```
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

This is what I get when I type **lspci -v** 

```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Unknown device 82fe
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```


From what I've read in the forums, it appears to be a problem with the sound driver, but I don't have much experience with ubuntu, so it'd be unsafe to speculate too much :tongue:

Please feel free to ask for additional information.  Any help would greatly be appreciated.


Thanks!

---

