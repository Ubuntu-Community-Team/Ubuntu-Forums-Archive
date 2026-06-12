---
title: "GRUB error 16"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-02-19
No sure what happened because my laptop was fine yesterday but when I tried to boot up today I got:

Grub 1.5
error 16

Ive searched around a little for this but I didn't get any definite answers. Id really appreciate any help.

---

### Post by caljohnsmith on 2009-02-19
From the Grub manual:
> **Error 16**: Inconsistent filesystem structure
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.
So probably the first thing to do would be to run a file system check on your Ubuntu partition. How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition sdaX (like sda5 for example), and then do:
```
[[ $(mount | grep [COLOR="Blue"]sdaX[/COLOR]) ]] || sudo e2fsck -fpv /dev/[COLOR="Blue"]sdaX[/COLOR]
```
Please post the output, and if the command completes successfully, how about rebooting and let me know if anything changes or not. We can work from there if you want.

---

### Post by Loki57701 on 2009-02-19
Well for some reason the error is gone. I shut down the computer for about 20min and when I turned it back on I had no problems, I even rebooted twice just to make sure. For now everything seems to be ok, Im not sure what could have caused it.
Thanks For the help though, I appreciate it.

---

