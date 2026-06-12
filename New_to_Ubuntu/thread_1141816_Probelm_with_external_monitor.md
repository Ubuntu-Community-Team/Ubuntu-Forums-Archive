---
title: "Probelm with external monitor"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Eberhard on 2009-04-28
Hey guys,

I've just installed 9.04 Jaunty and i'm having problems connecting my external monitor to my laptop. I dont want anything fancy such as dual screen or mirror - i just want to use one screen at a time. I'm using the GUI (Configure Display settings...) to change screen as i would in windows, turning the external screen on and laptop screen off. The external screen then displays what seems to be a 1280 x 1024 resolution squeezed to take up only the top 1280x768 of my screen.

The only time it works is in the log-in screen when i start up the computer with external screen pluged in - when I then log in the laptop display takes over.

Laptop:
HP dv1074ea (Intel graphics) w. VGA output
1280 x 768

External Screen:
1280 x 1024

I'm dual booting and it works 100% in windows.

I've searched the web without success. Hope you can help me

---

### Post by Eberhard on 2009-04-29
After many hours of internet search with no results I finally tried to disable desktop effects and this was all it took to solve my problem. Switching back an forth between my monitors now works like a charm with all resolutions.

This of course raises the question: Is it a bug with compiz?

---

### Post by Eberhard on 2009-04-30
After changing the resolution when everything looks bad, as described in the original post, all it takes is just to restart compiz. This can be done by.
```
compiz --replace
```

---

