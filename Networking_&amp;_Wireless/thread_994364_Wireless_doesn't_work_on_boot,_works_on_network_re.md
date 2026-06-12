---
title: "Wireless doesn't work on boot, works on network restart"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by sippyCUP on 2008-11-26
Hey guys,

I'm running Ubuntu 8.04 on an HP Pavilion DV4000. It's got a 2200BG centrino wireless chip running the ipw2200 driver.

Nearly every time (I can't remember a single time in the last ~50 boots) I boot up Ubuntu, the keyring guy will ask me for the password for my home wireless connection, I will provide it, but will be unable to ping my router. I do the following to restore connectivity:

```
sudo /etc/init.d/networking restart
```

And 90% of the time I can ping my router and access the internet. The other 10% of the time, I have to "uncheck" networking in the tray, recheck it, and run the networking restart again, and/or restart my router.

It's not limited to my router, either (and I will reply with the model number shortly, it's a DLink but I am not at home and forgot the model number). I have to go through the same "init.d restart" procedure with any wireless connection. It didn't seem to always be this way, either.

Any ideas?

Thanks,
Eric

---

