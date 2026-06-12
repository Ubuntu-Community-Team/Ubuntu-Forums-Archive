---
title: "Touchpad not workin after disable and reboot"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by pressko on 2011-02-23
Hi guys,


I have laptop acer6920g with ubuntu 10.10. After pressing alt + f7 which is my short key for touchpad enable/disable and rebooting system it's not working anymore. I cant find it even in System - > Preferences - > Mouse.  

:confused: :confused:   Can u help me to make it working again ?

10x in advance :guitar:

---

### Post by komputes on 2011-02-23
Try going into the BIOS and try enabling the touchpad, or try going into the BIOS then press Alt-F7 and then save/boot.

There seems to be an open bug related to this issue:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/366783](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/366783)

I recommend subscribing to this bug and marking it as affecting you. There are basically two workarounds provided in this bug.

1) Purging and reinstalling the driver:
```
$ sudo apt-get purge xserver-xorg-input-synaptics
$ sudo apt-get install xserver-xorg-input-synaptics
$ sudo reboot
```

2) Add the kernel boot parameter "i8042.nomux".
For this you need to (as root) change the following line /etc/default/grub from:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux"
```Save the file. 

Then to propagate the changes, run the command:
```
$ sudo update-grub
```

---

### Post by pressko on 2011-02-23
10x man,



it's working  :)

---

