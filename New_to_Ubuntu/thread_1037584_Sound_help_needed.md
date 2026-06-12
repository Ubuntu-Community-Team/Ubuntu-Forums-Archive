---
title: "Sound help needed"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by bradwal on 2009-01-11
I've been trying to get the sound to work on Ubuntu 8.10 for the past week since my install but I can't figure it out on my own so hopefully one of you out there can help. Alsa recognizes my drivers but I don't even get system sounds. 

I've tried going through the "Comprehensive Sound Problems Guide", but none of the fixes have worked for me. 

 "aplay -l" gives - 


```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


If anyone out there has any idea of what I need to do, help would be appreciated.

---

### Post by vikramaditya on 2009-01-11
I'm no guru, but it appears you may have 2 audio "solutions" in your system.  You might want to try disabling any onboard audio in your system bios.  Ubuntu may then pick up the remaining device.  Just a thought...

---

### Post by bradwal on 2009-01-12
That sounds like a good idea, I don't know how to disable the integrated sound card though. My bios doesn't give an option to shut off a sound card. The only peripherals it gives is VGA, LCD screen power, wireless power, and a few others.

Is there a way to disable it through Terminal?

---

### Post by hivelocitydd on 2009-01-12
See the Below link to disable the sound card

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=6949](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=6949)

---

### Post by bradwal on 2009-01-19
Thanks for the help, but sorry I still can't figure it out. There is no option to disable an on board sound card in my bios. I might not have an on board sound card.

---

