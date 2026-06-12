---
title: "Ram - how to tell how much I have..."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Pappy1911 on 2009-01-15
I cannot find out how to access my computer (within Ubuntu) to determine how much ram I have..

Any help??? Thanks

---

### Post by abn91c on 2009-01-15
> **Pappy1911 said:**
> I cannot find out how to access my computer (within Ubuntu) to determine how much ram I have..

Any help??? Thanks
easiest way is to reboot and look in the bios, within Ubuntu open terminal and type ```
top
``` then look top left it will say **total mem**. press the** q** key to exit

---

### Post by 5BallJuggler on 2009-01-15
> **abn91c said:**
> easiest way is to reboot and look in the bios

Or click on System - Administration - System Monitor.

It will tell you on the 1st tab.

See screenshot:-

---

### Post by albinootje on 2009-01-15
> **Pappy1911 said:**
> I cannot find out how to access my computer (within Ubuntu) to determine how much ram I have..


Open a terminal, and type :
```

free -m

```

---

### Post by MockY on 2009-01-15
System - Administration - System Monitor
Click the System tab. The amount is listed on top under the Hardware header. Keep in mind that it will not list 4GB if you are running a 32-bit version of Ubuntu.

---

### Post by Pappy1911 on 2009-01-15
And there it is.....

Thank you everyone....

---

### Post by pansz on 2009-01-15
> **MockY said:**
> Keep in mind that it will not list 4GB if you are running a 32-bit version of Ubuntu.
Unless you installed the server kernel.

32-bit users can have 64GB memory support by simply install the server kernel, it would be something like apt-get install linux-server

---

### Post by albinootje on 2009-01-15
> **pansz said:**
> Unless you installed the server kernel.

32-bit users can have 64GB memory support by simply install the server kernel, it would be something like apt-get install linux-server

Indeed.

And this should be enough for that :
```

sudo apt-get install linux-image-server

```

---

