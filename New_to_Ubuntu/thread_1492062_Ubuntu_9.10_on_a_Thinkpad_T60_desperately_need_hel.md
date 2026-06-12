---
title: "Ubuntu 9.10 on a Thinkpad T60: desperately need help with getting sound to work"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by irena_gg on 2010-05-24
Dear everyone,

I have been running Ubuntu 9.10 on a Lenovo T60 for about half a year, and sound was ok (although I needed to restart the computer every time I would want sound for an youtube).

A few weeks ago it simply dissapeared, and I am desperately trying to bring it back. I tried to follow the instructions at the link below, but no luck
[http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/](http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/)

Here's more specifics:
uname -a
Linux IndianCreek 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 23 2010 for kernel 2.6.31-21-generic (SMP).

head -n 1 /proc/asound/card*/codec#*
Codec: Analog Devices AD1981

If anyone has any ideas with regards to what avenue I need to pursue (get rid of ALSA and go with OSS;  buy a different sound card) to get the sound back, I would remain indebted for life:)

Also, a link to the output of the ALSA script for my system:
[http://www.alsa-project.org/db/?f=d173c3d4d29e6432248db469d992f494a01e3cfe](http://www.alsa-project.org/db/?f=d173c3d4d29e6432248db469d992f494a01e3cfe)

---

### Post by Brandon Williams on 2010-05-24
I have never had any sound trouble with my T60p running stock ubuntu/xubuntu. I'm currently running 10.04. The output from most of the debugging commandslooks about the same as what you've got, except for the kernel (higher version, as expected) and alsa (lower version). Did you install a custom version of alsa? I wouldn't expect 9.10 to be running a newer version of alsa than 10.04.

One additional thing that occurs to me is that the T60p has hardware controls for volume and mute that don't always show up in the mixer controls, IIRC. Is it possible that the sound has been disabled somehow in the hardware? Do you see any indication that the system is attempting to adjust the mixer when you press the sound control buttons above the keyboard?

---

### Post by LowSky on 2010-05-24
My T60 works fine. I have never had sound isssues?

---

### Post by irena_gg on 2010-05-24
Brandon:
I intentionally installed the latest version of Alsa Driver, Library, and Utilities (1.0.23) thinking that my solve the problem. It didn't.

When I press the sound buttons above the keyboard, I get a very unpleasant squeak.
I can see the music files in RhythmBox being played, just that there is no sound at all.

---

### Post by irena_gg on 2010-05-25
Brandon,

just wanted to say a big THANK YOU again!
I was able to figure my sound last evening, it definitely helped to check the keyboard sound buttons.
After all the tweaking I had previously done, the thing that got the sound back was putting to minimum the 'Mic Boos' indicator in the Gnome Alsa Mixer.

---

### Post by Brandon Williams on 2010-05-25
Glad you got it working.

I have that problem with feedback any time I enable the microphone for use with a headset and forget to disable it again after unplugging the headset. The builtin microphone has too much bad interaction with the speakers in my experience.

---

