---
title: "What is my Sound Group? Having Issues with this...."
date: 2010-01-09
forum: New to Ubuntu
---

### Post by listerdl on 2010-01-09
Hi there

Basically I installed 910 on a new laptop and am having absolute nightmares trying to get the sound to work....

I have a dual boot to windows and sounds work perfectly there.

On a tutorial to fix the sound it asks me:

**Are you in the sound group? do you have permissions**

Please check the commands with sudo.

sudo aplay -l 

[COLOR="DarkRed"]>> THIS IS >> 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #[/COLOR]0

>> THEN >>

**check that you are in the sound group in /etc/group**

sudo adduser USERNAME sound

What is my USERNAME is it the bit after @ or before @ (I am referring to the default line on the terminal)

Thanks for all advice

Having a nightmare here.

---

