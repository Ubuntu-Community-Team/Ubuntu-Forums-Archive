---
title: "how to restore display driver"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by dman535 on 2008-12-16
So I have tried to install the latest ati driver on my d600 ati mobility 9000 and its not taking. I get a segmentation error when I try to run the aticonfg --intial command.

I am stuck on the low graphics mode and would liek to just restore out of series of drivers to what ubuntu intially installed when it was loaded.

Is there an easy way to do that - or is there an easy fix for the segmentation error?

Thanks

Derek.-

---

### Post by doobiest on 2008-12-16
you might want to try installing envy-ng depending on your ubuntu version. It's an automated script for video driver config. Works pretty decent.

apt-get install envyng-gtk

---

### Post by Tatty on 2008-12-16
To restore to the default settings for your machine:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The segmentation fault is worrying though.  It usually means one of three things:

1. There is a serious bug in the software (unlikely)
2. There is corruption to that software on your machine
3. There is a hardware issue on your machine.

Keep an eye to see if you get any more applications segfaulting.

---

