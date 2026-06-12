---
title: "Can Ubuntu Play .wav Files?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by yangt299 on 2009-02-08
I'm trying to play a .wav file using audacious and all the other soundtrack players available for ubuntu. However, these files do not play and they are all .wav files. Can ubuntu play .wav files or do these files need to be changed into .mp3 files? 

Thanks

---

### Post by Dougie187 on 2009-02-08
What player are you trying to use?

---

### Post by Therion on 2009-02-08
You need to install the win32 codecs.

Open a terminal and enter: ```
sudo apt-get install ubuntu-restricted-extras
```
Answer the prompts and you're good to go.

---

### Post by iKonaK on 2009-02-08
or
```
sudo apt-get install vlc
```
or
```
sudo apt-get install gnome-mplayer
```

---

### Post by houstonbofh on 2009-02-08
> **Therion said:**
> You need to install the win32 codecs.

Open a terminal and enter: ```
sudo apt-get install ubuntu-restricted-extras
```
Answer the prompts and you're good to go.
This will give you the codecs for all programs on your system.  This may be helpfull... [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by SuperSonic4 on 2009-02-08
Ensure you have the medibuntu repos before you do the above commands

---

