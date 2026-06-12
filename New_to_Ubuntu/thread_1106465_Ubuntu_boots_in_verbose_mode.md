---
title: "Ubuntu boots in verbose mode"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by pipposanta on 2009-03-25
Hi,
I deleted swap partition to make space on my disk but now when I boot the splash screens displays the bar for some secondds and the goes in verbose mode. I have already deleted the swap partition references in **/etc/fstab** and executed **sudo swapoff -a**.
What can I do?

---

### Post by jakupl on 2009-03-29
I would not delete the swap partition.

What is the output of ```
cat /boot/grub/menu.lst
```

---

