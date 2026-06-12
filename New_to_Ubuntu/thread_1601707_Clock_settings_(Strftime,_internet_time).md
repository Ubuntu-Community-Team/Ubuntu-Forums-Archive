---
title: "Clock settings (Strftime, internet time)"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by J V on 2010-10-20
I've been working on setting my clock up (In my panel) via gconf-editor...

So far my custom format is very nice:
```
%a %d %b <b>%H:%M:%S</b>%t%s
```

This gives me the day, date, time (highlighted) and timestamp...

What I want now is the internet time (.beats)

I could make a new clock applet and give it the "internet" format, but I want to keep it all in one applet to keep one button and one uniform system... Unfortunately strftime doesn't support internet time, is there any way I can do some math wizardry in the format entry to pull the .beat?

---

