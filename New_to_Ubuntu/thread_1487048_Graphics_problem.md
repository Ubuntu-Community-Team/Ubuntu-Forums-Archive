---
title: "Graphics problem"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by Vistz on 2010-05-18
I turned on my laptop and I got an error saying that it would be running in low graphics mode. When I logged on, I tried to change the NVIDIA settings and got this: 

```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

---

### Post by Chesamo on 2010-05-18
In Terminal, run "sudo nvidia-xconfig".

---

### Post by Vistz on 2010-05-18
This is what I got:

```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

---

### Post by Chesamo on 2010-05-18
Now reboot.

---

### Post by Vistz on 2010-05-18
I'm running into the same problems. Before I log on, I get this error message:

```
Ubuntu is running in low-graphics mode. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:  system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error
(EE) No drivers available
```

---

### Post by Vistz on 2010-05-18
I have a question, I'm trying to download the latest drivers from the NVIDIA website. When I run ```
uname -r
```

I get ```
2.6.31-20-generic
```

Since I'm not sure which one to download, should I use the drivers by System>Administration>Hardware Drivers or install them manually?

---

