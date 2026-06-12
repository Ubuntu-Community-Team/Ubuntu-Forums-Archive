---
title: "atheros ar5b93 random disconnect"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by chaos_efphect on 2009-11-27
so its been awhile since i used ubuntu and i am a little lost, i just got a new gateway NV52 and everything works great expect my wifi. when the pc first turns on it connects with a very weak signal and then after about 20 mins it drops off and will not reconnect unless i reboot. i am at a total loss on this one.



btw i had the notebook sitting on my linksys router at one point and only got 1 bar. in windows tho the signal is normal and i don't have any of these issues.

Please Help :(

---

### Post by chaos_efphect on 2009-11-28
wow no one has any help?

---

### Post by sandyd on 2009-11-28
> **chaos_efphect said:**
> wow no one has any help?
```

_iwconfig_ _wlan0_ _rate_ _5.5M_ _auto_

```

---

### Post by drpjkurian on 2009-11-28
Hi
please let me know the output of ```
lshw -C network
```

---

