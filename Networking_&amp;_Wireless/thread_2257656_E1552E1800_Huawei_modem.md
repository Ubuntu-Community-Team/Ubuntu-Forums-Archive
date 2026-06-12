---
title: "E1552/E1800 Huawei modem"
date: 2014-12-21
forum: Networking &amp; Wireless
---

### Post by georgewsmit on 2014-12-21
Good day,

I have searched for the past 3 days to remedy my proble, found many post regarding the same problem but could not get it sorted out. I am on the point where I need help t do this!

I installed Ubuntu 12.04 on my lapton, and now I need to connect to the internet with my laptop using Huawei E1552/E1800 HSPA modem. 

I have tried various ways and followed many post and could not get it right. Maybe I do not understand so well... Can someone please assist me getting this modem sorted?


Kind regards
George

---

### Post by mörgæs on 2014-12-23
You need to tell exactly what you have tried and the results. 'I did something, help me' is not the best foundation for an answer.
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

I am not an expert in networking but general advice when problems appear is installing a later release like 14.04.1 or 14.10.

---

### Post by georgewsmit on 2014-12-24
> **mörgæs said:**
> You need to tell exactly what you have tried and the results. 'I did something, help me' is not the best foundation for an answer.
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

I am not an expert in networking but general advice when problems appear is installing a later release like 14.04.1 or 14.10.

Hi
Thanks for the reply. I have done so many things that I eventually re-installed Ubuntu12.04 from scratch.
I have no idea as to where to start and end with this and started again...


Here is what I have done: (The output of this first command is after I did all tese steps...)

```

takkies@takkies-laptop:~$ lsusb
Bus 001 Device 011: ID 12d1:1436 Huawei Technologies Co., Ltd. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:3121 Atheros Communications, Inc. 
Bus 001 Device 004: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink)

```

then:

```

takkies@takkies-laptop:~$ sudo rmmod usb-storage

```

then

```

takkies@takkies-laptop:~$ sudo modprobe usbserial vendor=0x12d1 product=0x1446

```

then
```

takkies@takkies-laptop:~$ sudo chmod -x /usr/sbin/usb_modeswitch

```

Hope this helps! If there is more info needed I will gladly give it...


Thanks for the help

---

### Post by mörgæs on 2014-12-25
If you already reinstalled why did you choose 12.04?

---

### Post by georgewsmit on 2014-12-27
Because that was the distro I had on disk. Just downloaded 14.04 now  and will  see what the outcome is.

---

### Post by georgewsmit on 2014-12-27
Ok, I just installed Ubuntu 14.04 LTS with the 3g dongle inserted. It actually installed by itself and is now fully opperational!
Thanks for the help. Much appreciated

---

### Post by mörgæs on 2014-12-27
Good, please spread the word (and mark the thread 'solved').

---

