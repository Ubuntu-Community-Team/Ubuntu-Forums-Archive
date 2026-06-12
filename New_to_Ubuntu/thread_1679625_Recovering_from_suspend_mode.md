---
title: "Recovering from suspend mode"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by lanzi on 2011-02-01
Hi guys,

as I´m fairly new to using Ubuntu I couldn´t get this fixed myself. Fresh install of Ubuntu 10.10 on my Asus UL30vt yesterday, everything worked as a charm - until i tried suspending it. It takes like, 35-50 sec for the system to recover from the suspend mode and around 15-20 sec to switch from gui to the first terminal (Ctrl+Alt+F1). Haven´t had these problems before - but no additional graphic drivers installed either (hybrid graphics solution). I thought it might have something to do with the graphic drivers (Nvidia 256.53) but I´m not too sure. Been googling for some time now but haven´t gotten any further. I attached the pm-suspend.log.

---

### Post by cariboo on 2011-02-01
Hibernate is extremely slow, I personally just close the lid on my netbook and it goes to sleep, it usually comes back again in less than 5 seconds. If you need hibernate, I would suggest you have a look at tuxonice, it's in the repositories.

---

### Post by lanzi on 2011-02-01
Hey Cariboo,
you probably misunderstood me. I *am* trying to get the laptop to sleep (Ubuntu folks named it "suspend") and awake right away - pretty much instantly. Hibernation is something else of course. That worked before, on my older installation. However, now it simply takes the login screen far too long to appear and is totally unpractical (using it during my lessons daily) as mentioned above.

---

### Post by ubuntoide on 2011-03-04
Same problem here, I just installed the .38 kernel and suspend is again fully working :)

---

