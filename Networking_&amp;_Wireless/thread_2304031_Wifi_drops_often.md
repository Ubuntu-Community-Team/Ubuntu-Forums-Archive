---
title: "Wifi drops often"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by jesse43 on 2015-11-23
I've been having a problem with my wifi dropping every so often. I really only use my laptop for Netflix so it's obvious when it drops. I haven't timed it but I don't think it's happens after so long. One thing to note that may lead to the cause is every time the screen starts to dim the wifi gets dropped. My fix is turn wifi off then on and it will connect right away. Pinging google works when the wifi is dropped. It says it's still connected so maybe it's not and has google cached somewhere. Any ideas?

---

### Post by ajgreeny on 2015-11-23
You do not tell us what wifi adapter chip you have, which might help, and you can get from command ```
lspci
```, but I suspect that this may be wifi power-management that is causing the problem and needs turning off.
See [http://ubuntuforums.org/showthread.php?t=1686641](http://ubuntuforums.org/showthread.php?t=1686641) for more details, which I think is still current even though it is a fairly old thread.

---

### Post by sammiev on 2015-11-23
Likely not a power option, but you can set your screen display never to dim in the power settings.

Right under that is the shut off Wi-Fi to save power.

---

### Post by jesse43 on 2015-11-23
lspci -k gives
```
0e:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
    Subsystem: Hewlett-Packard Company Device 1851
    Kernel driver in use: atl1c

```

dmesg | grep atl1c gives
```
[    2.133105] atl1c 0000:0e:00.0: version 1.0.1.1-NAPI
[    2.133700] atl1c 0000:0e:00.0 enp14s0: renamed from eth0
```

---

### Post by jesse43 on 2015-11-23
Setting the display to never dim wouldn't really help because the problem sometimes happens even when the screen isn't starting to dim.

And the setting underneath that turns my wifi off.

---

### Post by sammiev on 2015-11-23
> **jesse43 said:**
> One thing to note that may lead to the cause is every time the screen starts to dim the wifi gets dropped.

I added that because of your quote in your 1st post.

---

### Post by jesse43 on 2015-11-24
Oh yea. I mentioned that because maybe there is some event that happens every time the screen starts to dim like turning off wifi? Thought it might give a hint as to what's causing my issue. But turning dimming off won't fully solve my problem because it still happens sometimes when my screen isn't dimming. Thank you though.

---

