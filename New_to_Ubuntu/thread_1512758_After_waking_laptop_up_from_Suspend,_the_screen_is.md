---
title: "After waking laptop up from Suspend, the screen is dim and it wants a password"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by diablo75 on 2010-06-18
My fiancé has a Compaq Presario CQ60, which works with Ubuntu 10.04 pretty well.  Can't wait to see Plymouth get things fixed with the way it runs on nVidia chipsets, but anyway...

The thing will go into Suspend after a while of not using it (which is fine) but when you wake it back up, the brightness of the LCD is as dim as it can be and you have to use the Fn-F8 key combo to turn it back up to bright.  Not sure why this is.

Also, somewhat off topic, it will ask for a password to be typed in (she wishes it didn't do that too).

---

### Post by Naggobot on 2010-06-18
I could tell a really long story but I try to cut it short. 

I had a suspend resume problem and while debugging it I stumbled upon files

> /user/lib/pm-utils/video-quirks/20-video-quirk-pm-<manufacturer>.quirk.db
Now it may be that quirk

> --quirk-reset-brightnessmight help you if placed in a correct files / position. 

There is a way to suspend from command line with a quirk to test the quirk. I have tried it my self but could not find with quick googling. I'll post the comand if I find it.

Edit:
Found it
[http://en.opensuse.org/Pm-utils#Triggering_suspend_manually](http://en.opensuse.org/Pm-utils#Triggering_suspend_manually)

Note the warning. My quess/remembrace is that you can add the quirk option after command i.e.

```
sudo pm-suspend --quirk-reset-brightness
```

---

