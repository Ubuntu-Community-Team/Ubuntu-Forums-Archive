---
title: "Install flash on a 32-bit system"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by eddski on 2009-09-13
I'm trying t install flash on a 32-bit system. I'm having a difficuly time as most posts are 64-bit, please help!

---

### Post by Sealbhach on 2009-09-13
I would recommend you run this command in a terminal, it install most of the multimedia plugins that you will need:

```


sudo apt-get install ubuntu-restricted-extras
```

.

---

### Post by eddski on 2009-09-13
I tried that and it said I already have the newest version installed and that nspluginwrapper is no longer needed. But I still cannot play flash videos even everything is allowed in firefox.

---

### Post by QIII on 2009-09-13
Check to see that you DO NOT have swfdec or gnash installed.

If you do, remove them.  They cause conflicts with Flash.

---

### Post by kansasnoob on 2009-09-13
> **eddski said:**
> I tried that and it said I already have the newest version installed and that nspluginwrapper is no longer needed. But I still cannot play flash videos even everything is allowed in firefox.

So, did you run 'sudo apt-get autoremove' to get rid of it?

Also go to Synaptic, click on Search, then type "flash" and as stated previously make sure no swfdec-* or gnash packages are installed.

Remember Firefox must be restarted every time a change is made!

---

