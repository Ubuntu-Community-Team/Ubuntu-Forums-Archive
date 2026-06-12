---
title: "Is it possible to control the order of the startup programs?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-04-26
I'm wondering if there was a way to control the order in which the startup programs launch themselves?

I'm asking because I want emerald, then fusion-icon and then my screenlets to start in this order since having the screenlets starting before fusion-icon just makes a funny visual effect whereas starting in order its cooler. 

Thanks!

---

### Post by unutbu on 2009-04-26
Perhaps make a bash script:

```
#!/bin/sh
emerald &
sleep 1
fusion-icon &
sleep 1
screenlets &
```

(Change the commands as necessary. You can find the correct commands by clicking System>Pref>Sessions and clicking on each item's Properties button). You may or may not need the sleep commands.

Make it executable, and then click System>Pref>Sessions and remove the individual items for emerald, fusion-icon and screenlets. Add an item for the script instead.

---

### Post by wizard10000 on 2009-04-26
> **sylvainrb said:**
> I'm wondering if there was a way to control the order in which the startup programs launch themselves?

I'm asking because I want emerald, then fusion-icon and then my screenlets to start in this order since having the screenlets starting before fusion-icon just makes a funny visual effect whereas starting in order its cooler. 

Thanks!

There used to be but there isn't now unless you use the workaround unutbu listed above or something like it.  That bug is still open with GNOME.

---

### Post by sylvainrb on 2009-04-29
Thanks for the help and info. The script does the trick.

---

