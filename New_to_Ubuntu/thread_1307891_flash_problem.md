---
title: "flash problem"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by jasiek84 on 2009-10-31
Hi!

Something is very wrong with the flashplugin I installed.
I tried to re-install it, uninstall it, remove it and nothing works, and I can download anything from the software-center becaus of the flashplugin...
This is what I get when I try to download anything: E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.: 

Also I can open synapaptic because of the flashplugin package..

Please help me!

---

### Post by mac9416 on 2009-10-31
Hi there!

These commands should take care of it:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

---

### Post by jasiek84 on 2009-10-31
It worked perfectly!
Thank you so much!!

---

