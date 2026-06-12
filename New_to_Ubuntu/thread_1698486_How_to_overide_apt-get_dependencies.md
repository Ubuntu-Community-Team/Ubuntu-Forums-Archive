---
title: "How to overide apt-get dependencies?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Mariane on 2011-03-02
Hi, 

I've had to completely remove pulse-audio from my old computer because it was causing nothing but problems. This machine only works fine with alsa. 

The problem is, when I use apt-get to remove pulse-audio it also removes ubuntu-desktop. I would like to keep this, even with no sound. I sometimes use it for troubleshooting. For example it makes it easy to find nvidia drivers. 

I would like a command roughtly similar to : 
```

sudo apt-get install --ignore-depends ubuntu-desktop

```
but which would not really ignore them but ask me for confirmation each time. So I would say "yes" for everything except if the name contains "pulse". 

Please tell me how to write this. 

Mariane

---

### Post by TeoBigusGeekus on 2011-03-02
[This]("https://wiki.ubuntu.com/PulseAudio"). Scroll down to pulse audio removal.

---

### Post by oldos2er on 2011-03-02
It's safe to remove ubuntu-desktop. the only time you might need it would be if you upgrade to a newer version of Ubuntu.

---

