---
title: "Wireless mouse slowing system down"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by swvan on 2010-11-05
I have a gear head 2.4ghz optical wireless nano mouse that works perfect in WinXP. Ubuntu 10.10 recognizes the mouse and it works great for about 5 to 10 minutes and then the movement and system slows down to a crawl. When this happens I can still use the touchpad on my laptop which works at normal speed, but the wireless mouse never recovers. Any ideas?

---

### Post by ubudog on 2010-11-05
You probably did already, but try changing the batteries.  

If you did already, and it's still the same, wait until the mouse gets slow and open a terminal window. (Applications>Accessories>Terminal)

Post the output of:
```
dmesg
```

The dmesg command shows the most recent system logs, and we might be able to find the problem there.

---

### Post by Hippytaff on 2010-11-05
+1 ubudog
```

dmesg | less

```
easier to read :-)

---

### Post by ubudog on 2010-11-05
> **Hippytaff said:**
> +1 ubudog
```

dmesg | less

```
easier to read :-)

Yeah. :) 

Any results OP?

---

### Post by swvan on 2010-11-05
Will do as soon as it acts up again. Of course it is running fine right now!

---

### Post by Hippytaff on 2010-11-05
Maybe it was batteries then :-)

Also
```

dmesg | less

```
is really annoying unless you really want to scroll through the resulting output...so for posting follow ubudods advice```

dmesg

```
without the | less bit

---

