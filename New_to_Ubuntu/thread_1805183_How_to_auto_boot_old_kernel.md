---
title: "How to auto boot old kernel"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by smittypaddler on 2011-07-15
This morning I allowed Update Manager to install kernel 2.6.32-33-generic, and on the reboot it froze.  Thanks to a second laptop I was able to get here and found exactly what I needed to get to the old kernel:

0. Boot the ubuntu 10.04 install disk and tell it I wanted to recover a system.  It gave me a shell in my filesystem.

1. Look in /boot/grub/grub.cfg to find the entry for the old kernel, which in my case was 2.6.32-32-generic, third one in the list (2 relative 0).

2. Change /etc/default/grub to GRUB_DEFAULT=2.

3.  run update-grub

4.  Ctrl-D to exit the shell and reboot.  It works!

Many thanks to rnerwein who posted the solution.

---

