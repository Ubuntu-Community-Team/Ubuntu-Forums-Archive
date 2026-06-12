---
title: "simple boot"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by silvernitrate on 2009-06-04
Hey guys i have 9.04 and wanted to know if anyone knows how to shut off the splash screen so i can see whats going on during boot up

---

### Post by dje on 2009-06-04
**This will turn the splash off for every boot**
In a terminal (Applications >> Accessories >> Terminal):
```
gksudo gedit /boot/grub/menu.lst
```
In menu.lst look the first entry beneath "## ## End Default Options ##" and on the kernel line, remove the word splash (and quiet) and save the file

**This will only turn the splash off for one boot**
This can also be done only once at boot up by pressing Esc to get into the grub menu then pressing the e key to edit the boot sequences and remove the word splash (and quiet) from the kernel line. There are instructions at the bottom of the screen and it is fairly self explanatory

hope that helps,
dje

---

### Post by sti11_learning on 2009-06-04
To disable the splash screen run "sudo gedit /boot/grub/menu.lst" from a terminal. Then go to the entry for ubuntu and remove splash and quiet from the root line and quiet from the bottom. It should look something like this when you are done:```

title           Ubuntu 8.10, kernel 2.6.27-14-generic
uuid            926671ae-c157-4b68-b46e-1f8ff6a64937
kernel          /boot/vmlinuz-2.6.27-14-generic
root=UUID=926671aec157-4b68-b46e-1f8ff6a64937 ro
initrd          /boot/initrd.img-2.6.27-14-generic

```
As opposed to this:```

title           Ubuntu 8.10, kernel 2.6.27-14-generic
uuid            926671ae-c157-4b68-b46e-1f8ff6a64937
kernel          /boot/vmlinuz-2.6.27-14-generic
root=UUID=926671ae-c157-4b68-b46e-1f8ff6a64937 ro **quiet splash**
initrd          /boot/initrd.img-2.6.27-14-generic
**quiet**

```

**Oops someone beat me to it.**

---

