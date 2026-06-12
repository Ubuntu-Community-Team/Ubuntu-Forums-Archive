---
title: "verizon wan dongle not working in 10.04"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by ub9876 on 2010-10-17
I just loaded 10.04    my 3g dongle isnt working..  I got modeswitch and installed...  what do I need to get it working..??

---

### Post by Sealbhach on 2010-10-17
Is it a usb dongle? If so, plug it in and run lsusb in the terminal so we can see more info. Copy and paste result of lsusb in your reply, thanks.

.

---

### Post by ub9876 on 2010-10-17
jon-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jon-laptop:~$

---

### Post by Sealbhach on 2010-10-17
It's not showing up there. Is it definitely USB? Try booting up, with the USB already plugged in, then running lsusb.

.

---

### Post by ub9876 on 2010-10-18
got it going with a hard reset

---

