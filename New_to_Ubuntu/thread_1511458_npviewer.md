---
title: "npviewer"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by oz. on 2010-06-16
My first post... probably the wrong section.

I'm having problems with npviewer.bin I'm guessing it's some sort of Flash adaptation for Linux. I can live with it crashing when I close some image/video heavy internet sites - Youtube, QuakeLive, Hotmail is awful for it.

The problems I'm more worried about are my CPU temperatures. I think it is down to npviewer being to heavy on the processor. It's an AMD Dual-core 2.0GiB which isn't that old and it doesn't seem to be that bad looking at others on the market. It has a large heatsink with a 12cm fan clipped to the side. So I'm surprised by my heat problems.

Average temp is about 31/32deg with the fans on minimum. When I start watching videos I have to turn the fans up to full and hope it doesn't cook. Highest I've seen in the past week has been 42deg. This can't be good for the CPU if I keep lifting the temp to this level.

Is there any thing I can do to limit the usage or change something physically to keep the CPU cool? I enjoy Ubuntu for it being reliable and fast (and it's anything but Microsoft) but if this keeps up then I might be forced to revert back to Windows XP and keep away from the porn.

---

### Post by cariboo on 2010-06-17
42° is more than normal, I frequently see temps in the high 50's when doing cpu intensive activities, like transcoding DVDs.

As long as you core temps aren't getting close to 100°C you have nothing to worry about.

Running **sensors** in a terminal will give you the critical temps eg:

```
temp1:       +41.0°C  (high = +100.0°C, hyst = +96.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
```

---

