---
title: "VLC  now has no sound but Movie player etc still work fine"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by cpcpcp on 2011-07-31
[SIZE=2][COLOR=DarkGreen]What have I done, what do you think is the cause?[/COLOR][/SIZE]

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio DAC   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[SIZE=2][COLOR=DarkGreen]Ubuntu LTS 10.04
VLC 1.0.6[/COLOR][/SIZE]

Chris

---

### Post by Untold on 2011-07-31
It could be the file.  The same thing happened to me the other day.  I just opened it with another media player and it works fine.  Check out [http://www.umplayer.com/](http://www.umplayer.com/) I think you will be happy with it.  I have tried a few files that VLC skips around on and it works great.:guitar:

---

### Post by amjjawad on 2011-07-31
First step I would do is to remove it and re-install it again.

---

### Post by cpcpcp on 2011-08-01
> **Untold said:**
> It could be the file.  The same thing happened to me the other day.  I just opened it with another media player and it works fine.  Check out [http://www.umplayer.com/](http://www.umplayer.com/) I think you will be happy with it.  I have tried a few files that VLC skips around on and it works great.:guitar:
Good idea but it is not the file as VLC plays it (admittedly a Windows version) on another machine.

VLC is playing NO files with sound including .mp3 files.

---

### Post by cpcpcp on 2011-08-01
> **amjjawad said:**
> First step I would do is to remove it and re-install it again.

[SIZE=2][COLOR=DarkGreen]I have done that once already thinking it was the equivalent to turning a computer off, waiting and then turning it back on again.
I might re-install at the weekend again if no one comes up with a different fix / diagnosis
[/COLOR][/SIZE]

---

### Post by cpcpcp on 2011-09-05
If it helps within VLC messages at level 2 I get this

p, li { white-space: pre-wrap; } [COLOR=#00008B]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]resampling stopped after 14908904 usec (drift: -9606)[/COLOR]

---

### Post by cpcpcp on 2011-09-07
Fixed it. <blush>
Went into System
Went to sound
Selected Applications tab - it was empty
Played something with VCL
Applications tab now showed VLC media player and a slider volume control
The volume control was at nil (left hand side) -don't ask me why or how 
Sliding the control to the right gave me sound again.

---

