---
title: "Alsamixer save settings"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Gulfvet91 on 2009-09-05
I can't seem to get Alsamixer to save the settings I put in.  Every time I re-boot my computer, I have to bring it up and take my Master volume off mute and re-set the level.  Is there any way to get it to stay put?

---

### Post by Liolikas on 2009-09-05
You have to use alsa daemon for settings save at shutdown and restore from save at boot. Aka old default way I think Ubuntu have sth new pulse etc., but still I am alsa User on Gentoo.

---

### Post by Gulfvet91 on 2009-09-05
So how do I use Alsa Daemon?

---

### Post by snowpine on 2009-09-05
Set the audio settings how you want them, then open a terminal and:

```
sudo alsactl store
```

---

### Post by Sir Jasper on 2009-09-05
Hi snowpine,

Thank you for the code. I had the same problem until I used it. 

My regards

---

### Post by Gulfvet91 on 2009-09-19
Snowpine,
                   Your fix worked for a little while but on my system it keeps forgetting I saved those settings.

---

