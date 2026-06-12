---
title: "No sound in Linux 10.04 (Lucid Lynx)"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2010-10-08
Hey everyone, I just installed Ubuntu 10.04 and I absolutely love it. There's just one problem... no sound. Everything else works awesome save for a few things I think I can tweak myself.

I've done quited a bit of research on this issue and what I've seen is a lot of people saying that my "mute" button might be pushed in the volume control panel. 

I've made sure that the mute button is NOT checked in every conceivable volume control panel.

Any suggestions? They would surely be appreciated.

Also, I'm a total newbie, so you're going to have to explain things the way you would to a 5 year old. Thanks!

---

### Post by sandyd on 2010-10-08
> **Ranger_Joe said:**
> Hey everyone, I just installed Ubuntu 10.04 and I absolutely love it. There's just one problem... no sound. Everything else works awesome save for a few things I think I can tweak myself.

I've done quited a bit of research on this issue and what I've seen is a lot of people saying that my "mute" button might be pushed in the volume control panel. 

I've made sure that the mute button is NOT checked in every conceivable volume control panel.

Any suggestions? They would surely be appreciated.

Also, I'm a total newbie, so you're going to have to explain things the way you would to a 5 year old. Thanks!
a) did you check
```

alsamixer
```

b)
post output of
```

aplay -l
```

c) 
post output of
```

lspci 
```

---

### Post by gordintoronto on 2010-10-08
Yes, please tell us about your audio hardware.  Accessories/Terminal and the command lspci will identify it.

---

### Post by Ranger_Joe on 2010-10-11
Hey Guys, looks like this is solved. I upgraded to 10.10 (Maverick) and saw that the mute button was checked in ALSA Mixer. So, like before I unchecked it. I then went to Pandora, not expecting to hear anything.

Much to my surprise, I heard Kid Cudi. Thanks Ubuntu.

---

