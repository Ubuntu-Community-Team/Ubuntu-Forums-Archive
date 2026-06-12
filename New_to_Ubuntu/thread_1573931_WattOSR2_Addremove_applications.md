---
title: "WattOSR2 Add/remove applications"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by GoblinSlayer on 2010-09-13
Hello,

I've just installed WattOSR2. As far as I can see, there isn't an "Add/remove applications" application.

If someone would be able to guide me through the process of finding/installing it, this would be greatly appreciated.

Thanks,

GS

---

### Post by Nanix on 2010-09-13
If you open the menu, then go under "System Tools" you will find Add/Remove and the Synaptic package manager. These will allow you to do what you want.

This image shows the exact place:
[http://www.raiden.net/images/articles/wattos/desktopv.png](http://www.raiden.net/images/articles/wattos/desktopv.png)

---

### Post by GoblinSlayer on 2010-09-13
Yes, that's where I looked first. Unfortunately, when I highlight system tools, I see only "PCman filemanager" and "pyneighborhood".

The screenshot looks like a different distribution of WattOS. The version I'm using is shown here:

[http://www.planetwatt.com/index.php](http://www.planetwatt.com/index.php)

Thanks,

GS

---

### Post by ugm6hr on 2010-09-13
Try:
```
sudo apt-get install software-center
```

LXDE should be add it to the menu automatically after a reboot.

---

### Post by GoblinSlayer on 2010-09-13
Done.

I see:

```
Processing triggers for python-central ...
Setting up apport-gtk (1.13.3-0ubuntu2) ...
Processing triggers for python-support ...
Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```at the end.

Do I reboot now?

Thanks,

GS

---

### Post by ugm6hr on 2010-09-13
When it's finished installing.

---

