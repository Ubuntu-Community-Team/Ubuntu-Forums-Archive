---
title: "Wireless hard blocked"
date: 2017-10-29
forum: Networking &amp; Wireless
---

### Post by ferto2 on 2017-10-29
Im a total newbie to Linux. Ive just installed Ubuntu and all is fine. Only it seems like works networks are hard blocked and im not sure what to do about it. I've tried the first few things that came up in a Google search and none of it worked

---

### Post by ferto2 on 2017-10-30
Okay, I actually managed to undo the hard block. But still cannot see or connect to wifi networks.

[https://pastebin.com/raw/izSeEkFq](https://pastebin.com/raw/izSeEkFq)

---

### Post by ajgreeny on 2017-10-30
Dual boot with Windows or single boot Ubuntu only?

If dual boot, is Secure-boot disabled?

---

### Post by ferto2 on 2017-10-30
single boot with ubuntu only.

---

### Post by ferto2 on 2017-10-30
And now it seems it is once again hard blocked. :/

---

### Post by ferto2 on 2017-10-30
It seems like everytime I reboot it hard blocks again.

---

### Post by jeremy31 on 2017-10-31
See the wireless script in my signature and post results

---

### Post by praseodym on 2017-10-31
Can you activate wireless permanently in your BIOS/UEFI? Or resetting BIOS (not UEFI!) to default?

---

### Post by ferto2 on 2017-11-03
> **jeremy31 said:**
> See the wireless script in my signature and post results

[http://paste.ubuntu.com/25879053/](http://paste.ubuntu.com/25879053/)

So it seems like I solved the problem of hard blocking. But still, Wicd just doesn't recognize any networks.

---

### Post by praseodym on 2017-11-03
For the soft block:
```

sudo rfkill unblock all
```

---

### Post by jeremy31 on 2017-11-03
The script result still shows a hard block, does this computer have a switch to enable/disable wireless?

---

