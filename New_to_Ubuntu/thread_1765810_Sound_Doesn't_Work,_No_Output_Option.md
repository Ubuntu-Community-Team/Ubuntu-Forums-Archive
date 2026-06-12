---
title: "Sound Doesn't Work, No Output Option"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by R-Z on 2011-05-23
Well, I've got a laptop here that has no sound it seems. I have 11.04 on it, fully updated as of about 3 hours ago. I started with some of the easier stuff, and checked for the semi-obvious (muted and such). However, I noticed something when I went into the Sound Preferences into the Output tab, it only had 'Dummy Output' on the list.

Then I did a search about people with similar issues, and found one that said to use the ```
aplay -l | grep card
``` command to check and see what sort of sound card you've got in. Well, I did and this is what I got:

```
aplay: device_list:261: snd_ctl_pcm_next_device
```Supposedly I should have gotten a list of my sound devices in this?

PS: Just as a side note, it's actually entirely possible this thing doesn't have a sound card in it, though fairly unlikely. And I'm pretty new to Ubuntu, so it could be something painfully obvious I'm missing, though I did set up another one almost identical to this one, with no issues.

EDIT: Dropped to 10.10, worked fine. Dunno what was wrong.

---

