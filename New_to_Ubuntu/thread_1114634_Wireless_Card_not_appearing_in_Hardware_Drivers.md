---
title: "Wireless Card not appearing in Hardware Drivers"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Nemo137 on 2009-04-03
I installed Ubuntu via Wubi just now. I used the liveCD to check and make sure all my hardware worked with Ubuntu and every time the Hardware Drivers gave me a notification that I needed firmware for my wireless card and then helped me download and install it. Once I installed Ubuntu in windows with Wubi, however, that notification disappeared, and Ubuntu does not seem to be detecting a wireless card at all. I looked in the wireless forum, and all the threads there seem to start with the assumption that Ubuntu agrees that you have a wireless card. 

Is there a way to turn on the wireless card in settings that I'm missing? I'd be grateful for any help.

---

### Post by jlhaslip on 2009-04-03
have a look at System > Administration > Hardware Drivers ???
It may auto-detect and supply the Driver. Worked for me.

---

### Post by Nemo137 on 2009-04-03
That was the first place I looked. It's not there, and I'm wondering if there's another reason why it's not being picked up.

Thank you for your advice, though.

---

### Post by lkraemer on 2009-04-03
Open a Terminal window and d:
```

lshw -C network
ndiswrapper -l 
iwconfig

```
Then post the output here.

lkraemer

---

