---
title: "Oops I messed up grub!"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Torp3x on 2011-03-24
I installed startup manager to get some more pleasing resolution on my boot loader. Startup manager basically just messed things up, and couldn't restore it to normal. So I found some instructions on editing grub, which I followed, and now I get booted into tty...? 

So I can't get into Ubuntu right now, is there an easy way to restore grub from the live cd? I still have all the options at boot for Ubuntu, recovery mode etc. Hopefully someone will have a simple method of getting this fixed. :)

Thanks.

Ubuntu 10.10

Easily solved- Booted into recovery mode, low graphics, opened terminal to edit grub and initramfs to undo changes, updated grub and initramfs, rebooted- all good :)

---

