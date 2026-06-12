---
title: "swap area glitch!"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-10-03
I had defined 512MB of swap area at the time of installation but currently system monitor is showing 1.1 GB of swap area. How to fix it?

Thank You in advance...

---

### Post by NoaHall on 2009-10-03
It's probably using your ram as swap, if you have more than 3GB on a 32 bit version. It doesn't need fixing.

---

### Post by eshant_engineer on 2009-10-03
I have 2.5 GB RAM and using 64 bit version...

---

### Post by NoaHall on 2009-10-03
Hm. Do you have more swap on another hard drive? Maybe a swap file?

---

### Post by arrange on 2009-10-03
Could you post the output of```
free
sudo parted -l | grep swap
dmesg | grep -C2 swap
```

---

### Post by Paqman on 2009-10-03
> **NoaHall said:**
> It's probably using your ram as swap

Wut?

---

### Post by NoaHall on 2009-10-03
Sorry, I meant if he had more ram on his 32 bit system, it would allocate the spare ram to do other things.

---

### Post by eshant_engineer on 2009-10-03
command: free
 ```

             total       used       free     shared    buffers     cached
Mem:       2531928    1549012     982916          0     108748     607132
-/+ buffers/cache:     833132    1698796
Swap:      1155084     132548    1022536


```

command: sudo parted -l | grep swap
```
 2      12.9GB  13.4GB  535MB   primary   linux-swap
```

Command: dmesg | grep -C2 swap

```
[    2.214632] Write protecting the kernel read-only data: 6688k
[    2.232170] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.290579] compcache: Compressed swap size set to: 632984 KB
[    2.291522] TLSF: pool: ffffc20000072000, init_size=16384, max_size=0, grow_size=16384
[    2.299347] vesafb: framebuffer at 0xa0000000, mapped to 0xffffc20008380000, using 6144k, total 7616k
--
[    2.568532] e100 0000:05:08.0: PME# disabled
[    2.569545] e100: eth0: e100_probe: addr 0xb0000000, irq 20, MAC addr 00:16:76:d2:2f:3a
[    2.659011] Adding 632980k swap on /dev/ramzswap0.  Priority:100 extents:1 across:632980k
[    2.872055] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.031577] usb 2-1: configuration #1 chosen from 1 choice
--
[   13.805641] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   19.944676] lp0: using parport0 (interrupt-driven).
[   20.048525] Adding 522104k swap on /dev/sda2.  Priority:-1 extents:1 across:522104k
[   20.595529] EXT4 FS on sda1, internal journal on sda1:8
[   21.573860] type=1505 audit(1254562474.857:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2118

```

---

### Post by arrange on 2009-10-03
As you can see you're using [compcache]("http://code.google.com/p/compcache/").

---

### Post by eshant_engineer on 2009-10-03
Thanks to all experts...

---

