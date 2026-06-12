---
title: "Reinstallation: Will my /home partition get wiped?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Igniteflow on 2009-02-15
I currently have separate partitions for /filesystem, /swap and /home.  I'd like to do a fresh reinstall of the file system, but I'm worried that if I select the /home partition during re-installation that it will wipe it - which I really don't want to happen.  Could anyone tell me if this is the case? Or will it leave my data on /home intact?

Thanks in advance:guitar:

---

### Post by Elfy on 2009-02-15
You have to select it to give it the correct mountpoint - /home - but so long as you don't tick the format box then it will be untouched and mounted in your new install

---

### Post by Dies on 2009-02-15
It will do whatever you tell it to.

So make sure you pick expert or custom partitioning and select to format only the root partition and nothing else. As long as there isn't a check next to your home partition your fine.

---

### Post by NewJack on 2009-02-15
> **forestpixie said:**
> you have to select it to give it the correct mountpoint - /home - but so long as you don't tick the format box then it will be untouched and mounted in your new install

+1

---

