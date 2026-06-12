---
title: "cannot find php binary, php-5.3.6, installed from source"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by z5um on 2011-07-20
hola

today i installed lampp stack from source. Now i need to know where to find the php binary executable. I want to put it in my shell enviroment. I looked at php/bin and initiated some find commands but i simply cannot find it. Where is it ?

 When i install php via apt get, would it be a different php installation without connection to my lampp stack ?!

---

### Post by Primefalcon on 2011-07-20
> **z5um said:**
> hola

today i installed lampp stack from source. Now i need to know where to find the php binary executable. I want to put it in my shell enviroment. I looked at php/bin and initiated some find commands but i simply cannot find it. Where is it ?

 When i install php via apt get, would it be a different php installation without connection to my lampp stack ?!
try doing this

```
sudo updatedb; locate php | grep bin
```

---

### Post by z5um on 2011-07-20
very nice command, i was able to locate it instantly. It resides in php/bin -.-

---

### Post by Primefalcon on 2011-07-20
> **z5um said:**
> very nice command, i was able to locate it instantly. It resides in php/bin -.-
Your very welcome :-)

---

