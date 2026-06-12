---
title: "how to blacklist floppy drivers?"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by outleradam on 2010-11-13
I have a device which is detected as a floppy disk.  In order to proceed, I need to know how I can link a file in /dev/ to it's driver.  Where is the paper trail?

---

### Post by Hippytaff on 2010-11-13
Do you want to remove the driver from the blacklist?

If by paper trail you mean logs then you can find them in /var/logs

```

cd /var/logs

```
```

ls

```

and looking into modprobe will help with installing drivers :-)
Hope this helps...or maybe I've totally misunderstood :-S

---

### Post by outleradam on 2010-11-13
No, I want to blacklist the floppy driver because I have another device which is being improperly detected as a floppy.  I would like to know how to figure out what driver /dev/fd is using.

---

### Post by Hippytaff on 2010-11-14
```

lsmod

```
will list the drivers and give some info on what is using them :-)

---

