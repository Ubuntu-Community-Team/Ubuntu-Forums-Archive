---
title: "grub bootloader"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by 16sinker on 2009-04-08
What is the terminal command to determine which kernel I am booting from? I've updated to Jaunty beta and i think I have the latest kernel, but when I restart grub shows the older kernel from Intrepid.

---

### Post by zerhacke on 2009-04-08
uname -a

---

### Post by Tralce on 2009-04-08
```
uname -a
```
That will tell you the current kernel version.

---

### Post by 16sinker on 2009-04-08
This is th output of the command "uname -a"

bofus66@ubuntudell:~$ uname -a
Linux ubuntudell 2.6.27-14-generic #1 SMP Fri Mar 13 18:00:20 UTC 2009 i686 GNU/Linux
bofus66@ubuntudell:~$

Ihave just taken updates with update manager. That update included linux header, image and kernel 2.6.28-11 generic but I'm not booting from that kernel in grub. Any advice?

---

### Post by zerhacke on 2009-04-08
If I'm not mistaken you have to actively tell it to use the new kernel at least once during boot.  Press ESC during GRUB loading and it'll let you select a kernel to use.

---

### Post by 16sinker on 2009-04-08
When I hit escape to get to the bootloader the only two kernels available are 2.2.2.27-14 and 2.2.27-11.

---

### Post by 16sinker on 2009-04-08
Edit: that's 2.6.27-14 and 2.6.27-11. Sorry.

---

### Post by 16sinker on 2009-04-08
In past dists. the latest kernel appeared at the top of the boot list automatically. In ths case the new kernel, generic image, headers etc. appear in synaptic but not in the bootlist when I click esc to access grub. Is this because the new Jaunty kernel won't be available until the release candidate?

---

