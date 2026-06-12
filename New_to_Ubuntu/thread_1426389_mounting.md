---
title: "mounting"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by msidhard on 2010-03-10
i have a doubt friends, last time i installed ubuntu 9.10 . at that time i used automatic partition table. but now i always want to mount my drives manually. how could i recover from the problem. i want those drives should be mounted automatically when i start the system. and also i want to know . if we connect any thing to usb , we can find it by typing lsusb in terminal, but i want to know what device is connected and in what name it is mounted in /dev.thanx in advance. have anice day

---

### Post by mikewhatever on 2010-03-10
> **msidhard said:**
> i have a doubt friends, last time i installed ubuntu 9.10 . at that time i used automatic partition table. but now i **always want to mount my drives manually**. how could i recover from the problem. i want those **drives should be mounted automatically** when i start the system. and also i want to know . if we connect any thing to usb , we can find it by typing lsusb in terminal, but i want to know what device is connected and in what name it is mounted in /dev.thanx in advance. have anice day

First you say you want to mount the drives manually, then, that you want them automounted. Well, what do you want? Are those usb drives?
You can easily view all that's mounted by issuing one of the following commands:

mount

df -h

Best of luck.

---

### Post by laffinet on 2010-03-10
Excellent guide to mounting at startup (fstab) [here]("http://ubuntuforums.org/showthread.php?t=283131").

---

### Post by msidhard on 2010-03-11
friends i have a problem and a doubt. the problem is " i want my hard drives to be mounted automatically during start up" my doubt is " if i connect any thing like mouse or mobile or some thing through usb, how can i identify that in what name the thing is connected in /dev, example if i connect my mobile to usb and i type lsusb in terminal it shows"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0421:04bc Nokia Mobile Phones 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
"
i want to know in what name the nokia mobile is registered in /dev/ ex:/dev/ttyusb0, . i think u will understand.

---

