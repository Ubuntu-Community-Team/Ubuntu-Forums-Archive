---
title: "sound card issue"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by dhirajkhanna on 2010-11-06
No sound after upgrading to Maverick. lspci -v identified my sound card as 
Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
Don't know how to configure this in the sound preferences.

---

### Post by 4ll41 on 2010-11-06
Can you post output of $ aplay -l  command?

- Have just solved my sound issues following this [one]("http://ubuntuforums.org/showthread.php?t=1046137"), check it out

---

### Post by dhirajkhanna on 2010-11-06
This is the output

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by dhirajkhanna on 2010-11-06
now what?

---

### Post by 4ll41 on 2010-11-07
There are several things that can be the reasons for not having sound. Try System --> Preferences --> Sound and check if everything is not muted. Also in Hardware tab how many devices do you see? If two, check your sound by selecting each one of them.


Otherwise, type in a terminal: 

```
 cat /proc/asound/version 
```

You can see the ALSA version you are using. If smaller than 1.0.23 I would advise you to upgrade it by using the guide I sent you above in this page [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137).

Good luck

---

