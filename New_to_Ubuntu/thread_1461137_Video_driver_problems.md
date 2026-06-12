---
title: "Video driver problems"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by Sunfist on 2010-04-23
This may be hard to track down as it doesn't happen very often, but sometimes when I start Ubuntu it starts without (or it appears that way at least) loading the Nvida drivers for my video card. I have to reboot it, sometime more than once, to get it to start up with the screen looking the way it should. Is there a command I can use that will show me the driver that Ubuntu is currently using, so I can verify if it is in fact not using the Nvida driver, or if it may be some other problem? Any other troubleshooting tips for when this happens again?

---

### Post by achase79 on 2010-04-23
This may be fixed by saving a xorg.conf file out of nvidia-settings.
hit alt-f2 and type "gksu nvidia-settings" and select "x server display configuration" and click the "save to X Configuration File"
This should make sure the computer always uses your nvidia driver every time

---

### Post by Sonsum on 2010-04-23
the command

```
lspci | grep VGA
```

will tell you your video card model.

If we know that, it might make solving your problem a little easier.

---

