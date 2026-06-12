---
title: "Ndiswrapper &amp; BCM4318"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by jdralphs on 2007-04-06
I'm working on someone's laptop right now & I'm running inot a problem getting the wifi working.

The laptop is a HP dv8000 & the wifi is a Broadcom BCM 4318

I have Ndiswrapper installed with the correct drivers

The problem is that when I try to sudo modprobe ndiswrapper,

I get this output:

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid Argument
```

ndiswrapper -v output:
```
utils Error: no version specified!
driver version                 1.22
vermagic:                      2.6.17-11-generic SMP mod_unload gcc-4.1
```

uname -r output:
```
2.6.17-11-generic
```

Any ideas?

---

### Post by spd106 on 2007-04-06
Check out this guide, step 13 is probably what you need (you might not need to download a new version of ndiswrapper). [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

i.e.
Try ```
sudo apt-get install ndiswrapper-utils-1.8 
``` or grab the package from here [http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.8](http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.8) and doubleclick on it.

---

