---
title: "Black Screen on startup"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Scott753 on 2009-11-18
Hello, I recently installed ubuntu 9.10 on one of my older machines and got the following problem.

After the installation, everything was fine, I installed mediaubuntu, some other programs, etc. The problem occurred when I tried to reboot. 

I get the Grub loaded, I select normal boot. Then the ubuntu logo shows up for a few seconds, then a black screen. And for some reason, my keyboard doesn't work either. 

Oh, and the recovery mode works, except there isn't a GUI, just a command line.

I'm a ubuntu newbie, so any help would be greatly appreciated.

---

### Post by Scott753 on 2009-11-19
Oh, btw, my computer is so old that I don't remember its specs. If there's a command that would help me figure that out, please let me know.

---

### Post by ukripper on 2009-11-19
> **Scott753 said:**
> Oh, btw, my computer is so old that I don't remember its specs. If there's a command that would help me figure that out, please let me know.

When you get to your login screen where it blacks out, press CTRL + ALT + F1 and then put your username and password.


Run this command and post output here:
```
xrandr
```

---

### Post by sandy8925 on 2009-11-19
You can use the lspci and lshw commands to find out your comp's specs. lsusb will list the USB devices currently connected. lsmod will give you the list of kernel modules currently loaded (it's not exactly what you asked for but could be useful in some situations)

---

