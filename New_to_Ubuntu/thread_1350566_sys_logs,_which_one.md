---
title: "sys logs, which one?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Paul T. on 2009-12-09
I'm having intermittent graphics problems which I'm trying to track down the cause of by looking at the system logs, but there are so many logs to trawl through, which one would give me some clues?

---

### Post by bswilson on 2009-12-10
It kind of depends on your problem.  However, the X server sends its data to a file called Xorg.#.log (where # is the older versions).  Try this command to view the latest information:

```
sudo cat /var/log/Xorg.0.log
```

or 

```
sudo tail /var/log/Xorg.0.log
```

---

