---
title: "I think I know why my internet service is so slow since upgrading to 9.04"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by audit on 2009-04-28
When I start up my computer it seems to be connecting to my internet service twice (wlan1 Bit Rate=2 Mb/s , and wlan0 Bit Rate=54 Mb/s). This if my assumption is correct is why my service has become so slow since since upgrading to 9.04.
Am I experiencing a bug? How do I stop it from doing this? Any help appreciated.

---

### Post by barbedsaber on 2009-04-28
mine has also been slow, how did you find out what connections are active, so I can check mine.
Thanks.

---

### Post by northern lights on 2009-04-28
> **barbedsaber said:**
> mine has also been slow, how did you find out what connections are active, so I can check mine.
Thanks.

```
iwconfig
```

For more in-depth info, read [man iwconfig]("http://linux.die.net/man/8/iwconfig")

---

### Post by barbedsaber on 2009-04-28
/facepalm
I knew that, how did I not remember that.
(feels stupid)

---

