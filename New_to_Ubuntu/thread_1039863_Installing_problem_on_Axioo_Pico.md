---
title: "Installing problem on Axioo Pico"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by kukeluk on 2009-01-15
haloo all..
i have netbook axioo Pico..
when i want to install it appears this message

```

udevd-event[1448]: run_program: '/sbin/modprobe' abnormal exit
[  43.804589] SGI XFS ACLs, security attributes, realtime, large block numbers, no debug enabled
[  43.804589] SGI XFS Quota Management subsystem
[  43.823282] JFS: nTxBlock = 8007, nTxLock = 64057

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

than, i cant continue my installation..
thanks before..:popcorn:

---

### Post by Crafty Kisses on 2009-01-15
Not sure what version of Ubuntu you are trying to install but depending on the hardware you might need to use a more recent version of Ubuntu, or compile a newer kernel. For the time being, I need more information, so post the results of these commands via LiveCD:
```
lsusb
lspci
lspci -vvnn
dmesg
```

---

### Post by kukeluk on 2009-01-15
i try to install Ubuntu 8.04
i already use LiveCD, but, is useless..after linux kernel loading appear that message..

any idea?

---

### Post by Crafty Kisses on 2009-01-15
What are your system specs?

---

### Post by feel_free on 2009-08-08
Hi
I Had install Ubuntu 8.04 (hardy) on my netbook axioo pico djj, as you know pico dont have optical drive on standar so you must buy it 1st. but you can install ubuntu hardy with usb, you need netbootin to make usb boot.

---

