---
title: "Bizarre White Bars and Ubuntu will not boot"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Rny2 on 2010-02-20
Alright, I really got myself in over my head on this one.

I was messing around with Compiz and compositing and such. My computer lags from the new changes and the screen freezes, so I manually reboot. After rebooting, I no longer have title bars. I messed around a bit more, re-enabled Compiz (which got me back my compositing, but not my title bars), and rebooted again.

Now, after getting past the grub screen, all I get are two horizontal lines of about 2 cm long, on the upper half of my screen. Nothing else happens.

Anyone have a clue what might be broken/ what can be done?

---

### Post by stoogiebuncho on 2010-02-20
Try booting into recovery mode and select the option to drop to a root terminal.

The compiz configuration files are kept in /home/USERNAME/.compiz (I'm pretty sure... you may want to wait for someone else to confirm this).

I would try deleting the .compiz folder.  Once you're in the root terminal, enter the command

```

rm -r /home/USERNAME/.compiz

```

then reboot
```
reboot
```

As I said before, this is what I would try if I was in your situation, but depending on how cautious you are feeling, you may want to wait until someone else confirms that this is a good idea.

---

