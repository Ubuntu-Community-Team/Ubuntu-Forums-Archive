---
title: "Geforce MX400 proprietary driver enabled,but not working"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Ben_222 on 2010-02-28
I did an install to the entire IDE hd of a desktop with Ubuntu 9.10,and boot to the HD.Then I went to Hardware,and downloaded the driver for this card(InVidia Geforce MX400 AGP 128Mb) .So it was enabled then.I restarted and it is not working,and I am in low graphics mode.I searched some for this card in the forums,but have not seen this problem.Can someone help?

---

### Post by cariboo on 2010-03-02
Try starting in recovery mode, once at the menu select drop to root prompt. At the prompt type:

```
nvidia-xconfig
```

the above command will create a new /etc/X11/xorg.conf file, and backup the old one. Once the new file is created type:

```
reboot
```

at the prompt, it should then boot to your desktop.

---

