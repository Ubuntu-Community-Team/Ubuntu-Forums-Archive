---
title: "bluetooth pairing, missing files"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by jamaas on 2007-04-24
If I have the following packages loaded on Efty 
bluetooth
kdebluetooth
bluez-utils

should I also have the file 

/usr/bin/bluez-pin  ?

I don't seem to, don't know where I went wrong.

Suggestions?

Thanks

Jim

---

### Post by bnuytten on 2007-04-24
```
aptitude install bluez-pin
```

---

### Post by jamaas on 2007-04-24
Thanks for this, now how can I see if is discoverable, still can not find it with the phone.

Thanks

Jim
> **bnuytten said:**
> ```
aptitude install bluez-pin
```

---

### Post by bnuytten on 2007-04-26
> **jamaas said:**
> Thanks for this, now how can I see if is discoverable, still can not find it with the phone.

Have a look at [this thread about Bluetooth (not) being visible/discoverable]("http://ubuntuforums.org/showthread.php?p=2537951")

---

