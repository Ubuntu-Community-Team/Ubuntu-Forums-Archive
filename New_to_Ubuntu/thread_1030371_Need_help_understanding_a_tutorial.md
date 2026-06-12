---
title: "Need help understanding a tutorial"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by bradwal on 2009-01-04
No sound  is working on my computer right now so I've been searching around the forums and I've found a tutorial and a post that may help me out but need help understanding what to do and how to execute it. I think this step is what I need for a fix but I don't know how I specify my hardware device in the terminal command like it says to do -


"3. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a bug in Intrepid):

```
$ alsamixer [COLOR="Blue"]-Dhw[/COLOR]
```

Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer."

What do I type into terminal for that instead of "alsamixer -Dhw"?



I also may need to know how to disable a sound card's auto jack detect in Ubuntu-

[http://ubuntuforums.org/showpost.php?p=3335072&postcount=646](http://ubuntuforums.org/showpost.php?p=3335072&postcount=646)

The guy in that post has the same audio controller as me and said all he needed to do was disable auto jack detect to make the sound work. Does anyone know the command or instructions to disable auto jack detect?

---

### Post by bradwal on 2009-01-04
I guess I should include what my hardware device is too since that's what I'm wondering how to enter in- 



aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by kestrel1 on 2009-01-04
Have a look at this it may help:
[http://ubuntuforums.org/showpost.php?p=5017453](http://ubuntuforums.org/showpost.php?p=5017453)

---

### Post by bradwal on 2009-01-04
> **kestrel1 said:**
> Have a look at this it may help:
[http://ubuntuforums.org/showpost.php?p=5017453](http://ubuntuforums.org/showpost.php?p=5017453)

Thanks, it looks like that's what I needed. I think that pulled up my sound card and the master sound wasn't muted so I'm lost all over again now. Time to figure out what the next problem could be.

---

