---
title: "only 1 of my laptop speakers working..."
date: 2010-07-27
forum: New to Ubuntu
---

### Post by jmedoro on 2010-07-27
It sounds as if sound is only coming out of my bottom ('lapside') speaker of my laptop when using Ubuntu (doesnt happen for me in Windows). I'm not even clear on how many speakers my laptop has, as I've never thought of it before having this problem.

Anyone ever hear of this occurring, and know how to fix? I've already checked for posts involving laptop speaker problems, but none seem to address this.

Thanks!

---

### Post by cariboo on 2010-07-28
Open a terminal and type:

```
alsamixer
```

If you don't have alsa-utils installed Ubuntu will tell you what to do.

Once you have alsamixer running, use the arrow keys to navigate and turn volume up and down. Make sure the volume for your speakers are turned up.

Once you have things working satisfactorily, press esc to exit , then in the same terminal type:

```
sudo alsactl store
```

to save the settings, or else you will have to do it every time you reboot.

---

