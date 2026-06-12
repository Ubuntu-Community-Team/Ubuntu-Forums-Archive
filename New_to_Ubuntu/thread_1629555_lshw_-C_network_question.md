---
title: "lshw -C network question"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by vldster on 2010-11-23
[IMG]http://i2.photobucket.com/albums/y50/vldster/Screenshot.png[/IMG]
 
So out of all this output where do I find that the OS can use my wifi card?

---

### Post by papibe on 2010-11-23
> **vldster said:**
> 
So out of all this output where do I find that the OS can use my wifi card?

That is just to list what hardware has been recognized. Use iwconfig to configure your card. Good news is the "Atheros" chipset is, in general, well supported on Linux.

Good Luck!

---

### Post by mikewhatever on 2010-11-24
If the card is correctly recognized and the correct driver is loaded, chances are it will work.

---

### Post by nothingspecial on 2010-11-24
Type ```
lsmod | grep ^ath5k
```

If you get a result you should be fine.

---

