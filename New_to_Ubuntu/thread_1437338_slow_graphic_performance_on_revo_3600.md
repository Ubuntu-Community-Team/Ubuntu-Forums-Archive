---
title: "slow graphic performance on revo 3600"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by fulhamch on 2010-03-23
I have Just installed Ubuntu on my Revo 3600, and am experiencing very slow graphics performance when watching video both online and locally. Anyone else have this and any help?

thanks
ch

---

### Post by wojox on 2010-03-24
Have you checked System > Administration > Hardware Drivers for a video driver to be activated?

What type of videos are you watching? .avi, flash

Also what are you watching them in: Firefox, Totem?

May want to install from the terminal:

```
sudo apt-get update && sudo apt-get install non-free-codecs
```

---

