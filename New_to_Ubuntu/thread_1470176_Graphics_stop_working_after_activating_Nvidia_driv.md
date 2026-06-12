---
title: "Graphics stop working after activating Nvidia drivers"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Fenrisulfr on 2010-05-02
I have a 64-bit system running the 64-bit Ubuntu 9.10, I have an Nvidia Geforce 210.

Just freshly installed Ubuntu, and upon activating the proprietary drivers for the graphics (in System -> Administration -> Hardware Drivers) and restarting, I get an error saying the drivers won't load, and this:

```
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found
```I was able to get back to the state before that by taking out the xorg.conf from /etc/x11

and when I try to activate the drivers again, I get an error message

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

and upon looking in this log, these are the last lines in it:

```
"2010-05-02 13:58:25,503 WARNING: modinfo for module nvidia failed: 
2010-05-02 13:58:25,503 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting"
```

---

