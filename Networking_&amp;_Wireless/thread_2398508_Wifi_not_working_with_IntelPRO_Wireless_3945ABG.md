---
title: "Wifi not working with Intel/PRO Wireless 3945ABG"
date: 2018-08-13
forum: Networking &amp; Wireless
---

### Post by metalxer on 2018-08-13
Hello everybody,
I have installed Xubuntu 18.04.1 LTS on my HP Compaq 6710b, which has Intel/PRO Wireless 3945ABG, and it should work out of the box..but it doesn't. When I run lspci -nnk in terminal, among other things, I get this:
```
Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company PRO/Wireless 3945ABG [Golan] Network Connection [103c:135c]
18:00.0 Ethernet controller [0200]: Broadcom Limited NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Hewlett-Packard Company 6710b [103c:30c0]
    Kernel driver in use: tg3

```

I'd appreciate some help with this, thanks in advance.

---

### Post by chili555 on 2018-08-13
What is the result of:```
rfkill list all
sudo modprobe iwl3945
```Thanks.

---

### Post by metalxer on 2018-08-13
rfkill list all shows nothing, and after sudo modprobe iwl3945 I get this:
```
modprobe: ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open moddep file '/lib/modules/4.15.0-30-generic/modules.dep.bin'
modprobe: FATAL: Module iwl3945 not found in directory /lib/modules/4.15.0-30-generic
```

---

### Post by chili555 on 2018-08-13
Is the result the same if you do:```
sudo depmod -a
```Reboot.```
sudo modprobe iwl3945
```

---

### Post by metalxer on 2018-08-13
Yes, the result is the same. But when I type sudo depmod -a, I get this:
```
depmod: ERROR: could not open directory /lib/modules/4.15.0-30-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
```
EDIT: I should probably say that I've tried some things submitted in other similar threads, so it's possible that I've mixed something already. I'm completely new to Linux so I don't have the in-depth knowledge to know what I'm actually doing in terminal.

---

### Post by chili555 on 2018-08-13
Please try:```
sudo apt install --reinstall linux-image-4.15.0-30-generic
sudo update-initramfs -u -k all
```Reboot and try again:```
sudo modprobe iwl3945
```

---

### Post by metalxer on 2018-08-13
Okay, now I only get this after modprobe:
```
modprobe: FATAL: Module iwl3945 not found in directory /lib/modules/4.15.0-30-generic
```

---

### Post by chili555 on 2018-08-13
Let us see:```
sudo depmod -a
uname -r
sudo updatedb
locate iwl3945.ko
```

---

### Post by metalxer on 2018-08-13
Now uname -r gives me this:
4.15.0-30-generic

And locate iwl 3945.ko gives me [this]("http://txt.do/d7sol").

EDIT: I forgot to mention, after 
```
sudo apt install --reinstall linux-image-4.15.0-30-generic
sudo update-initramfs -u -k all
```
display resolution has changed to 1024x768 and I can't set up the native resolution of the display (1280x800). I suppose this has something to do with Intel drivers?

---

### Post by chili555 on 2018-08-13
Interesting. The module exists in the -29 kernel version but not -30. Please run:```
sudo apt install --reinstall linux-modules-4.15.0-30-generic
sudo modprobe iwl3945
```

---

### Post by metalxer on 2018-08-13
Okay, I had a little time on my hands and installed new Xubuntu alongside this one..and I'm really really sorry but it seems it was just me who was really stupid - while installing the first one I just clicked next when it asked me if I want to install third-party software for graphics, wifi, etc. (default option was 'no'). And now when I was installing new Xubuntu alongside the old one, it dawned on me and I checked this option, and now everything works flawlessly.
Again, sorry for bothering, but at least if someone has the same problem they know what was wrong.
Thanks for your time!

---

### Post by chili555 on 2018-08-13
Glad it's working by whatever means. Have fun!

---

### Post by jeremy31 on 2018-08-13
I actually think there was an issue when Ubuntu installed the 4.15.0-30 kernel and for some reason skipped the linux-modules-extra package install due to some error as this does happen once in a while

linux-modules-4.15.0-30-generic contains the tg3 module to support your ethernet but linux-modules-extra-4.15.0-30-generic has the iwl3945

---

