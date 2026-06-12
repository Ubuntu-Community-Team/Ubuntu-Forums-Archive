---
title: "Cannot boot into Windows XP"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by IsolatedSheep on 2009-11-07
Hello guys, I'm new to ubuntu.

Recently I installed Ubuntu 9.10 for dual boot. During the installation, I installed the grub inside sda1 which is where my XP is located. Now I can't do dual boot due to this mistake. How can i correct this? Btw, my XP files is still exist but just can't boot into XP. Thanks in advance. :)

---

### Post by NickJones on 2009-11-07
Just re-install Ubuntu onto the same Partition. Don't go into the advanced section on page 6.

---

### Post by IsolatedSheep on 2009-11-07
I'm not sure what page 6 is. I installed Ubuntu using the manual option. At my first try, I installed grub inside sda1, that's when the problem started. At boot, the Windows XP option is not listed as 'other operating system' but along with linux. Somewhat like this:
```
Windows NT/2000/XP (on /dev/sda1)
```And whenever i clicked the option, the only thing that would appear is this:
```
Grub &#9654;
```
I can't type anything. I can only press Ctrl+Alt+Del to reboot.

---

### Post by philinux on 2009-11-07
Run ubuntu and open a terminal.

```
sudo update-grub
```
There's is an outstanding bug where the grub installer fails to pick up the windows install.

---

