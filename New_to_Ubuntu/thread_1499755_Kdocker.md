---
title: "Kdocker"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by hifly1231 on 2010-06-02
Does anyone know how to change the time that Kdocker looks for the system tray from 5 seconds to 10 seconds in Lucid Lynx?  Thanks!

---

### Post by hifly1231 on 2010-06-24
So nobody knows how to increase the time that Kdocker waits to minimize an application to the system tray at startup?  I need to increase the time from 5 seconds to 10 or 15 seconds.

---

### Post by hifly1231 on 2010-09-12
OK, I've figured out how to delay Kdocker.  I've put in the command line (in "Startup Applications") - kdocker -d 20 -l sunbird.  But it's still not working!!!  I've input all the way up to -45, but still, Sunbird will open first, then I get the box stating "Could not find a matching window for Sunbird in the specified time: 20 seconds."  What am I doing wrong!!!  HELP!!!

---

### Post by hifly1231 on 2010-09-28
> **hifly1231 said:**
> OK, I've figured out how to delay Kdocker.  I've put in the command line (in "Startup Applications") - kdocker -d 20 -l sunbird.  But it's still not working!!!  I've input all the way up to -45, but still, Sunbird will open first, then I get the box stating "Could not find a matching window for Sunbird in the specified time: 20 seconds."  What am I doing wrong!!!  HELP!!!

Nobody knows what I'm doing wrong, or the correct way to accomplish this?

---

### Post by hifly1231 on 2010-11-12
That's OK.  I got the answer directly from KDocker.

---

### Post by Ms_Angel_D on 2010-12-05
So could you share your answer?

---

### Post by WestCoastSuccess on 2011-03-05
In case anyone comes across this problem, try the (seemingly undocumented) -y option:

```
kdocker -y thunderbird
```

If you want a decent sized icon for thunderbird:

```
kdocker -y -i /path/to/icon.png -q thunderbird
```

---

