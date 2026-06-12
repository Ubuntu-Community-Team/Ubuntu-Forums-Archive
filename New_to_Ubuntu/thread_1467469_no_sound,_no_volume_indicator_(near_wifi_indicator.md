---
title: "no sound, no volume indicator (near wifi indicator)"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by gwilkins82 on 2010-04-30
Upgraded to 10.04 with no big problems, but turns out there is no sound.  there is also no volume indicator up top to mess with.  any ideas?

ETA - with pulse audio, i can get playback fine via headphones...

Re ETA - I can actually get the audio to work through the speakers if i select analog headphones/no amplifier.  weird.

---

### Post by Doug11 on 2010-04-30
> **gwilkins82 said:**
> Upgraded to 10.04 with no big problems, but turns out there is no sound.  there is also no volume indicator up top to mess with.  any ideas?

ETA - with pulse audio, i can get playback fine via headphones...
Mine disappeared as well. I just went to Sound and Audio and drug my volume control to my panel where it used to be and locked it there. Which I like better cause it has all the preferences.

---

### Post by Sealbhach on 2010-04-30
Yes, it's a workaround. Go to System/Preferences, right-click on Sound and select "Add this launcher to panel".

.

---

### Post by melnichuk on 2010-05-25
Regarding sound indicator. Check if package "indicator-sound" isn't missing, if the package is missing use the following workaround:
```
sudo apt-get install indicator-sound
```

---

