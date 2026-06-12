---
title: "Ubuntu 10.4 not detecting monitor correctly."
date: 2010-08-07
forum: New to Ubuntu
---

### Post by digitography on 2010-08-07
Ubuntu 10.4 not detecting monitor correctly.

I have a Dell 450 workstation with a Radeon 7000 AGP card.

running under windows I can get the full res 1280 x 1024

with ubuntu I can only get 1024 x 768 or less, or the rather wacky 1360 x 768.

However occasionally I can get  1152 x 864, however ubuntu does not understand what the monitor is.

This is a recent install (yesterday 7 Aug 10) initially all was well ubuntu detected the monitor and gave full res. then update manager ran, after that the problems started.

I have searched the forum and there are many similar issues but none quite like this one.

help as always appreciated

---

### Post by sikander3786 on 2010-08-07
Hi.

Had you installed drivers for your graphics card before the update? Seems like the new kernel can't find drivers for your card.

Try *EnvyNG*. Remove the drivers and reinstall them.


```

sudo apt-get install envyng

```

And it will guide you through the rest of process.

Regards.

---

