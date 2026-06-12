---
title: "rf-monitor using zd1211rw"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by inoesomestuff on 2007-05-07
I was wondering if anyone knew what i was doing wrong, I am using a USB device that uses the zd1211rw driver (i think). according to the driver's website it should be able to enable monitor mode but when i go console and type:
```
>iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not permitted.
``` 
ive disabled networking and tried again (since i am currently connected) but i got the same result, any tips?

---

### Post by chili555 on 2007-05-08
Did you *sudo* that command?

---

### Post by inoesomestuff on 2007-05-10
thanks, that was silly

---

