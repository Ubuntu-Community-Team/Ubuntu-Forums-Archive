---
title: "iwl3945 driver?"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by zyon1989 on 2008-07-12
hey

first of al, im a newbie in linux.
I installed Ubuntu 8.04 on a usb (persistent).
I have a intel 3945abg card. My problem is that airmon-ng don't find myn driver (i think).
> Interface	Chipset		Driver

wlan0		Unknown		Unknown (MONITOR MODE NOT SUPPORTED)


I do can connect to the internet,so the card works...
What should I do to fix this?

---

### Post by chili555 on 2008-07-12
Some people claim the iwl3945 cannot be forced into monitor mode witha hammer. I say mine does, but I have to bring the interface down first:```
sudo ifdown wlan0
sudo iwconfig wlan0 mode monitor
```Afterwards, I can only get it back with:```
sudo rmmod iwl3945
sudo modprobe iwl3945
```Please try it and post back for the benefit of the searchers.

---

### Post by zyon1989 on 2008-07-12
i got this.

> glenn@ubuntu:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
glenn@ubuntu:~$ sudo iwconfig wlan0 mode monitior
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.


---

### Post by mamad876 on 2008-07-13
try:

sudo bash
... type password
ifconfig wlan0 down
iwconfig wlan0 mode monitor

---

### Post by zyon1989 on 2008-07-13
i found my problem

I installed aircrack with the apt-get, this installs version 0.93
I manualy installed 1.0-rc1 and it works.

---

### Post by Joker512 on 2008-10-16
I am having the same problem, Im pretyt sure i did the same thing you did but how do you manually install aircrack?

---

### Post by dorkizzle on 2008-10-16
> **Joker512 said:**
> I am having the same problem, Im pretyt sure i did the same thing you did but how do you manually install aircrack?

[http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=411680b5cc1e1d62a6f6fd4908c034aa](http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=411680b5cc1e1d62a6f6fd4908c034aa) :)

---

