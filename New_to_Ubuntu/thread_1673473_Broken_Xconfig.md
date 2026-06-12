---
title: "Broken Xconfig"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by jvslice on 2011-01-22
I have Ubuntu 10.10 running and had two monitors running on the box with a NVIDA graphics card.  I had to use the second monitor running on a nother machine and when I reset the PC I updated X for a single monitor, most likely did it wrong because when I rebooted I am at a shell prompt, no X windows.

---

### Post by cariboo on 2011-01-22
At the prompt type:

```
sudo nvidia-xconfig
```

The above command will create a new /etc/X11/xorg.conf file, which should get you back to your desktop.

---

### Post by jvslice on 2011-01-22
Thanks,

Everything x is back.

---

