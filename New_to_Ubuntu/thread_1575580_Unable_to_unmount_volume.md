---
title: "Unable to unmount volume"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by ricardisimo on 2010-09-15
"wineserver is busy with volume" or some such thing... but I never ran wine anything today or yesterday or at all since the last time I started the computer. I had to go into System Monitor and kill all of the wine processes before I could unmount my flash drive safely.

What gives? What could launch wine without me? Could a windows virus conceivably do something like this in Ubuntu? I did in fact try installing some Windows apps several days ago. Could it be?

---

### Post by CharlesA on 2010-09-15
What mountpoint/volume is it?

Try running this:

```
sudo lsof /path/to/mountpoint/or/volume
```

---

