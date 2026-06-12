---
title: "how to load a driver on startup?"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by outleradam on 2010-10-31
I have a ubuntu mini installation.  How can I ensure a driver is loaded on startup before my software starts?   I need to load the driver lirc_atiusb on system startup before software.

---

### Post by rockerphil on 2010-10-31
ok, here's how it works. unlike Windows where you have to install every little driver the machine requires Linux loads them as kernel modules and detects the vast majority of the hardware upon boot, so as long as the driver isn't for anything really out there you're more than likely loading it upon boot. this is why i can take a Linux hard drive out of a computer and put it in to another tower with different hardware configurations and it runs flawlessly 9 times out of 10. so in short, drivers are loaded from the core of the system when booted, not as a separate piece of software as in Windows. hope this helps,

Phil

---

### Post by outleradam on 2010-10-31
Look, the driver I need modprobed is not loading on startup.  It needs to load on startup.  I need to specify it.  How do I do that?

---

### Post by sandyd on 2010-10-31
> **outleradam said:**
> Look, the driver I need modprobed is not loading on startup.  It needs to load on startup.  I need to specify it.  How do I do that?

```

nano /etc/modules
```

---

### Post by outleradam on 2010-10-31
thanks.  that's what I needed.

---

