---
title: "afp server no longer visible in nautilus network tab?"
date: 2017-08-06
forum: Networking &amp; Wireless
---

### Post by eezacque on 2017-08-06
I have a MacBook laptop which used to be visible under the Nautilus network tab.
Now, while I can connect to it through 'Connect to Server' as afp://... , it is no longer visible under the Network tab.
No big deal, just a little annoying.

Any clue?

---

### Post by Morbius1 on 2017-08-06
Don't know much about afp but macOS services showing up under Network automatically are dependant on avahi in Linux.

Is avahi not running:
```
sudo service avahi-daemon status
```

---

### Post by eezacque on 2017-08-06
> **Morbius1 said:**
> Don't know much about afp but macOS services showing up under Network automatically are dependant on avahi in Linux.


Avahi is up and running. 

Thanks for thinking along.

---

