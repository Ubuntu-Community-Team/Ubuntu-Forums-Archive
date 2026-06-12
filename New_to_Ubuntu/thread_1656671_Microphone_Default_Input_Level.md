---
title: "Microphone Default Input Level"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by expatCM on 2010-12-31
I find that every time I start my pc the microphone input level is too low.  People cannot hear me on Skype until I move the slider (found at System / Preferences / Sound / Input) up from the default position of 100% to close to the maximum on the right.

Every time I shut down the setting goes back to 100%

How can change the microphone volume so that it stays where I set it from one session to the next?

---

### Post by TeoBigusGeekus on 2010-12-31
Try this from terminal.
```
alsamixer
```
Increase the input volume (or mic volume) and press Esc when done.
Then
```
sudo alsactl store
```
to make it permanent.

---

### Post by expatCM on 2011-01-01
Ah ...  the missing link .....  I did not know about alsactl store to save the settings ....  but now I do.   Thank you.

---

### Post by lidex on 2011-01-01
Skype has a configuration setting that allows it to adjust mic levels. If the above solution does not work, go into skype options and disable it.

---

