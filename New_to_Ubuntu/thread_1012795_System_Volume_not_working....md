---
title: "System Volume not working..."
date: 2008-12-16
forum: New to Ubuntu
---

### Post by LtPitt on 2008-12-16
Hello there!

I've been hassling with my installation for two days and now I have my sweet Intrepid Ibex on and rocking...
The only thing I miss is volume control :/

I have a LOT of peripherials to enable and/or disable if I press right click on the volume icon and choose preferences...
I just want the volume to go up and down if I click on it :|

I've been trying various combinations with no luck...
any hints? :(

---

### Post by Michael.Godawski on 2008-12-16
hi LtPitt, 

don't know where to start.
right click at the volume control, then open volume control, there you should have your up and down of the volume...


[LIST]
[*][https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[/LIST]

---

### Post by LtPitt on 2008-12-17
Correct!
But if I move it or mute it...

No effects at all!

---

### Post by LtPitt on 2008-12-17
Thanks to your link I've found out using

aplay -l

that I have

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Therefore if I choose with right click on volume control--->preferences---> i find a combobox and I choose ICH5 and then "Master".
But if I play an mp3 and change what now should be the master volume nothing happens...

Thank you for your support =)

---

### Post by LtPitt on 2008-12-17
Using alsamixer command from terminal I've found out that I should use PCM to lower volume!
It works! I'm HAPPY :D

Thanks!

This topic is solved :D


Ehm.
I don't know how to set the topic as solved :|
Maybe only the admins can do that?

---

