---
title: "kernel upgrade but cannot bot to that kernel"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by eddski on 2010-11-18
I did an upgrade to 2.6.35-22 and all parts(abi,config,initrd,system.map,vmcoreinfo,vmlinuz) are /boot but when I try to bot it from the grub menu, I get "error15: file not found", Ive checked menu.lst several times to make sure all the numbers matched up and they did. Its kind of frustrating, of all previous updates ive never had this problem. Thanks in advance.

---

### Post by amauk on 2010-11-18
Sounds like something's gone awry with the grub config

During boot, press and hold the shift key
you'll get the grub menu (with the new kernel selected)
use the arrow keys to select the previous kernel, and press enter to boot

Once logged in, do
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo update-grub
```

This will pull down all updates, and update the boot loader

Reboot and see if you can boot to the new kernel

---

