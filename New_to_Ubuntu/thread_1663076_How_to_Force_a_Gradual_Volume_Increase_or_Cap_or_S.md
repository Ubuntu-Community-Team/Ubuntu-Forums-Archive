---
title: "How to Force a Gradual Volume Increase or Cap or Similar?"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by jayi on 2011-01-09
Hello everyone. Ever since I started using ubuntu this month, I have been in love with it. However, I have a big issue... I think my bad clicking ability is making me deaf. Let me explain.

Many times the volume of a youtube video or something similar is too high or low so I will click the indicator applet at the top of my ubuntu to adjust the volume a little bit. However, MANY times I will accidentally click the far right part of my volume control or something similar and my volume will suddenly be 100% and my ears will start dying.

Is there any way to never allow myself to do this kind of thing? Maybe by not letting me increase the volume so much at one time and/or setting a much lower maximum volume? I have made this careless mistake many times and I'd like to do something before it becomes a problem for my health. I still have a headache from making this mistake again tonight. :(

---

### Post by cariboo on 2011-01-09
You can set the maximum volume in alsamixer, open an Applications->Accessories->Terminal and type:

```
alsamixer
```

use the arrow keys to navigate and adjust the volume. Once you have changed the settings to your liking, press esc to close alsamixer, then in the same terminal type:

```
sudo alsactl store
```

to save the changes you've made.

As an aside, I use the wheel on my mouse to change volume levels after clickong on the sound icon.

---

