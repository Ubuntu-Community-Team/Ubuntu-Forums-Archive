---
title: "permanent audacity failure after changing of temp folder --&gt; bug?"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by noob5000 on 2010-11-12
i changed the temp folder path in the audacity preferences (because the system partition was too small for a particular audacity project). when changing the path i got an error message and set the path back to the original folder. but ever since the pogram does not work anymore and another error appeared without me doing anything else than changing the temp folder path:
in the same preferences tab i cannot choose the sound applications anymore (alsa, pulse etc) because the dropdown menus for that are not readable anymore...

has anybody made similar experiences? how can i fix it and get audacity to work again?

sorry for posting this here, just doing so because posting seems to be disabled in the multimedia subforum.
(also i AM a beginner, using ubuntu only since 2009 and have no skills in the terminal nor any basic understanding of the system)

---

### Post by sandyd on 2010-11-12
> **noob5000 said:**
> i changed the temp folder path in the audacity preferences (because the system partition was too small for a particular audacity project). when changing the path i got an error message and set the path back to the original folder. but ever since the pogram does not work anymore and another error appeared without me doing anything else than changing the temp folder path:
in the same preferences tab i cannot choose the sound applications anymore (alsa, pulse etc) because the dropdown menus for that are not readable anymore...

has anybody made similar experiences? how can i fix it and get audacity to work again?

sorry for posting this here, just doing so because posting seems to be disabled in the multimedia subforum.
(also i AM a beginner, using ubuntu only since 2009 and have no skills in the terminal nor any basic understanding of the system)
```

rm -rf ~/.audacity-data
```

---

### Post by noob5000 on 2010-11-12
it worked! 1000 thanks!!! :guitar:

---

